---
tags:
  - code
  - code_snippet
  - autogen
  - large_language_models
  - agentic_ai
keywords: 
topics: 
language: python
date of note: 2025-04-04
---

## Code Snippet Summary

>[!important]
>Create conversable agents to **play chess**
>- Develop chess board
>- Develop legal move and make move functions
>- Register functions in agents
>- Call agents to make move 
>- Register nested chat


## Code

### Define Chess 

```python
import chess
import chess.svg
from typing_extensions import Annotated
```

### Initialize Chess Board

```python
board = chess.Board()
made_move = False
```

### Define Tools

- get legal moves

```python
def get_legal_moves(
    
) -> Annotated[str, "A list of legal moves in UCI format"]:
    return "Possible moves are: " + ",".join(
        [str(move) for move in board.legal_moves]
    )
```

- make a move

```python
def make_move(
    move: Annotated[str, "A move in UCI format."]
) -> Annotated[str, "Result of the move."]:
    move = chess.Move.from_uci(move)
    board.push_uci(str(move))
    global made_move
    made_move = True
    
    # Display the board.
    display(
        chess.svg.board(
            board,
            arrows=[(move.from_square, move.to_square)],
            fill={move.from_square: "gray"},
            size=200
        )
    )
    
    # Get the piece name.
    piece = board.piece_at(move.to_square)
    piece_symbol = piece.unicode_symbol()
    piece_name = (
        chess.piece_name(piece.piece_type).capitalize()
        if piece_symbol.isupper()
        else chess.piece_name(piece.piece_type)
    )
    return f"Moved {piece_name} ({piece_symbol}) from "\
    f"{chess.SQUARE_NAMES[move.from_square]} to "\
    f"{chess.SQUARE_NAMES[move.to_square]}."
```

### Create Player Agents

```python
from autogen import ConversableAgent
```

```python
# Player white agent
player_white = ConversableAgent(
    name="Player White",
    system_message="You are a chess player and you play as white. "
    "First call get_legal_moves(), to get a list of legal moves. "
    "Then call make_move(move) to make a move.",
    llm_config=llm_config,
)
```

```python
# Player black agent
player_black = ConversableAgent(
    name="Player Black",
    system_message="You are a chess player and you play as black. "
    "First call get_legal_moves(), to get a list of legal moves. "
    "Then call make_move(move) to make a move.",
    llm_config=llm_config,
)
```

```python
def check_made_move(msg):
    global made_move
    if made_move:
        made_move = False
        return True
    else:
        return False

```

```python
board_proxy = ConversableAgent(
    name="Board Proxy",
    llm_config=False,
    is_termination_msg=check_made_move,
    default_auto_reply="Please make a move.",
    human_input_mode="NEVER",
)
```

### Register the Tools

- A tool must be registered for the agent that calls the tool and the agent that executes the tool.

```python
from autogen import register_function
```

```python
for caller in [player_white, player_black]:
    register_function(
        get_legal_moves,
        caller=caller,
        executor=board_proxy,
        name="get_legal_moves",
        description="Get legal moves.",
    )
    
    register_function(
        make_move,
        caller=caller,
        executor=board_proxy,
        name="make_move",
        description="Call this tool to make a move.",
    )
```

```python
player_black.llm_config["tools"]
```

### Register the nested chats

- Each player agent will have a **nested chat** with the board proxy agent to
make moves on the chess board.

- [[Assistant Agent and Reflection and Nested Chat in AutoGen]]

```python
player_white.register_nested_chats(
    trigger=player_black,
    chat_queue=[
        {
            "sender": board_proxy,
            "recipient": player_white,
            "summary_method": "last_msg",
        }
    ],
)

player_black.register_nested_chats(
    trigger=player_white,
    chat_queue=[
        {
            "sender": board_proxy,
            "recipient": player_black,
            "summary_method": "last_msg",
        }
    ],
)
```


### Start the Game

- The game will start with the first message.

```python
board = chess.Board()

chat_result = player_black.initiate_chat(
    player_white,
    message="Let's play chess! Your move.",
    max_turns=2,
)
```




-----------
##  Recommended Notes

- [[Conversation Agent with ChatGPT]]
- [[AutoGen 0.2 Tool Use]]

- Coursera
	- [AI Agentic Design Patterns with AutoGen](https://www.coursera.org/learn/ai-agentic-design-patterns-with-autogen/home/week/1)

- Documentation
	- [Tool Use](https://microsoft.github.io/autogen/0.2/docs/tutorial/tool-use)