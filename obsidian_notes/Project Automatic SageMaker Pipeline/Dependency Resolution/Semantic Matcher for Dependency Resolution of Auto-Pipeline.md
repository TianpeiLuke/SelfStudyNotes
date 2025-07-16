---
tags:
  - code
  - code_snippet
  - aws/sagemaker_pipeline
  - amazon/mods_pipeline
keywords: 
topics: 
language: python
date of note: 2025-07-16
---

## Code Snippet Summary

>[!important]
>The **Semantic Matcher** is a specialized component that calculates semantic similarity between names using multiple matching algorithms. 
>- It plays a critical role in the *dependency resolution system* by enabling intelligent matching of *dependency names* and *output names* even when they are not identical.

- [[Dependency Resolver for Automatic Pipeline]]
## Code

```python
class SemanticMatcher:
    """Semantic similarity matching for dependency resolution."""
    
    def __init__(self):
        """Initialize the semantic matcher with common patterns."""
```

## Key Design Choices

### 1. Multi-Metric Similarity Calculation

>[!important]
>Rather than relying on a single matching algorithm, the matcher uses multiple complementary metrics to calculate a more robust similarity score:

```python
def calculate_similarity(self, name1: str, name2: str) -> float:
    """
    Calculate semantic similarity between two names.
    
    Args:
        name1: First name to compare
        name2: Second name to compare
        
    Returns:
        Similarity score between 0.0 and 1.0
    """
    if not name1 or not name2:
        return 0.0
    
    # Normalize names
    norm1 = self._normalize_name(name1)
    norm2 = self._normalize_name(name2)
    
    # Exact match after normalization
    if norm1 == norm2:
        return 1.0
    
    # Calculate multiple similarity metrics
    scores = []
    
    # 1. String similarity (30% weight)
    string_sim = self._calculate_string_similarity(norm1, norm2)
    scores.append(('string', string_sim, 0.3))
    
    # 2. Token overlap (25% weight)
    token_sim = self._calculate_token_similarity(norm1, norm2)
    scores.append(('token', token_sim, 0.25))
    
    # 3. Semantic similarity (25% weight)
    semantic_sim = self._calculate_semantic_similarity(norm1, norm2)
    scores.append(('semantic', semantic_sim, 0.25))
    
    # 4. Substring matching (20% weight)
    substring_sim = self._calculate_substring_similarity(norm1, norm2)
    scores.append(('substring', substring_sim, 0.2))
    
    # Calculate weighted average
    total_score = sum(score * weight for _, score, weight in scores)
    
    return total_score
```

>[!important]
> This approach provides several advantages:
> - **Robustness**: Different metrics capture different aspects of similarity
> - **Flexibility**: Weighting can be adjusted based on importance
> - **Resilience**: Works even when one metric fails to identify similarity
> - **Tuning**: Can be tuned for different naming conventions

### 2. Semantic Knowledge Base

The matcher maintains an internal knowledge base of domain-specific synonyms and abbreviations:

```python
def __init__(self):
    """Initialize the semantic matcher with common patterns."""
    # Common synonyms for pipeline concepts
    self.synonyms = {
        'model': ['model', 'artifact', 'trained', 'output'],
        'data': ['data', 'dataset', 'input', 'processed', 'training'],
        'config': ['config', 'configuration', 'params', 'parameters', 'hyperparameters', 'settings'],
        'payload': ['payload', 'sample', 'test', 'inference', 'example'],
        'output': ['output', 'result', 'artifact', 'generated', 'produced'],
        'training': ['training', 'train', 'fit', 'learn'],
        'preprocessing': ['preprocessing', 'preprocess', 'processed', 'clean', 'transform'],
    }
    
    # Common abbreviations and expansions
    self.abbreviations = {
        'config': 'configuration',
        'params': 'parameters',
        'hyperparams': 'hyperparameters',
        'preprocess': 'preprocessing',
        'eval': 'evaluation',
        'reg': 'registration',
        'pkg': 'package',
        'packaged': 'package',
    }
    
    # Stop words that should be ignored in matching
    self.stop_words = {'the', 'a', 'an', 'and', 'or', 'but', 'in', 'on', 'at', 'to', 'for', 'of', 'with', 'by'}
```

>[!important]
> This domain knowledge allows for much more intelligent matching:
> - **Domain Awareness**: Understands common ML pipeline terminology
> - **Synonym Recognition**: Recognizes equivalent terms like 'params' and 'parameters'
> - **Abbreviation Handling**: Properly handles abbreviations and expansions
> - **Stop Word Removal**: Ignores common words that don't contribute to meaning

### 3. Name Normalization

>[!important]
>Before comparing names, the *matcher* **normalizes** them to remove irrelevant differences:

```python
def _normalize_name(self, name: str) -> str:
    """Normalize a name for comparison."""
    # Convert to lowercase
    normalized = name.lower()
    
    # Remove common separators and replace with spaces
    normalized = re.sub(r'[_\-\.]', ' ', normalized)
    
    # Remove special characters
    normalized = re.sub(r'[^a-z0-9\s]', '', normalized)
    
    # Expand abbreviations
    words = normalized.split()
    expanded_words = []
    for word in words:
        expanded = self.abbreviations.get(word, word)
        expanded_words.append(expanded)
    
    # Remove stop words
    filtered_words = [word for word in expanded_words if word not in self.stop_words]
    
    return ' '.join(filtered_words)
```

>[!important]
> This **normalization process**:
> - Makes comparisons *case-insensitive*
> - Handles different *separator conventions* (`snake_case`, `kebab-case`, `dot.notation`)
> - Expands *common abbreviations*
> - *Removes noise words*

### 4. Specialized Similarity Metrics

>[!important]
>The matcher implements **four complementary similarity metrics**:

#### String Similarity

```python
def _calculate_string_similarity(self, name1: str, name2: str) -> float:
    """Calculate string similarity using sequence matching."""
    return SequenceMatcher(None, name1, name2).ratio()
```

>[!important]
>This uses Python's `difflib SequenceMatcher` to **calculate the overall string similarity**, which is effective at catching *minor spelling differences* and *transpositions*.

#### Token Similarity

```python
def _calculate_token_similarity(self, name1: str, name2: str) -> float:
    """Calculate similarity based on token overlap."""
    tokens1 = set(name1.split())
    tokens2 = set(name2.split())
    
    if not tokens1 or not tokens2:
        return 0.0
    
    intersection = tokens1.intersection(tokens2)
    union = tokens1.union(tokens2)
    
    return len(intersection) / len(union) if union else 0.0
```

>[!important]
>This calculates the **Jaccard similarity** between the sets of **tokens**, which is good at catching *word-level similarities* regardless of order.

- [[Jaccard Similarity and Jaccard Distance between Two Sets]]

#### Semantic Similarity
```python
def _calculate_semantic_similarity(self, name1: str, name2: str) -> float:
    """Calculate semantic similarity using synonym matching."""
    tokens1 = set(name1.split())
    tokens2 = set(name2.split())
    
    # Find semantic matches
    semantic_matches = 0
    total_comparisons = 0
    
    for token1 in tokens1:
        for token2 in tokens2:
            total_comparisons += 1
            
            # Direct match
            if token1 == token2:
                semantic_matches += 1
                continue
            
            # Synonym match
            if self._are_synonyms(token1, token2):
                semantic_matches += 0.8  # Slightly lower score for synonyms
    
    return semantic_matches / total_comparisons if total_comparisons > 0 else 0.0
```

>[!important]
>This leverages the **synonym knowledge base** to detect semantically equivalent words.

#### Substring Similarity

```python
def _calculate_substring_similarity(self, name1: str, name2: str) -> float:
    """Calculate similarity based on substring matching."""
    # Check if one is a substring of the other
    if name1 in name2 or name2 in name1:
        shorter = min(len(name1), len(name2))
        longer = max(len(name1), len(name2))
        return shorter / longer
    
    # Check for common substrings
    words1 = name1.split()
    words2 = name2.split()
    
    max_substring_score = 0.0
    for word1 in words1:
        for word2 in words2:
            if len(word1) >= 3 and len(word2) >= 3:  # Only consider meaningful substrings
                if word1 in word2 or word2 in word1:
                    shorter = min(len(word1), len(word2))
                    longer = max(len(word1), len(word2))
                    score = shorter / longer
                    max_substring_score = max(max_substring_score, score)
    
    return max_substring_score
```

>[!info]
>This detects when one name is contained *within another or shares common substrings*, which is useful for matching *abbreviated names* with their expanded versions.

### 5. Alias Support

>[!info]
>The matcher includes special handling for **aliases**:

```python
def calculate_similarity_with_aliases(self, name: str, output_spec) -> float:
    """
    Calculate semantic similarity between a name and an output specification,
    considering both logical_name and all aliases.
    
    Args:
        name: The name to compare (typically the dependency's logical_name)
        output_spec: OutputSpec with logical_name and potential aliases
        
    Returns:
        The highest similarity score (0.0 to 1.0) between name and any name in output_spec
    """
    # Start with similarity to logical_name
    best_score = self.calculate_similarity(name, output_spec.logical_name)
    best_match = output_spec.logical_name
    
    # Check each alias
    for alias in output_spec.aliases:
        alias_score = self.calculate_similarity(name, alias)
        if alias_score > best_score:
            best_score = alias_score
            best_match = alias
    
    # Log which name gave the best match (only for meaningful matches)
    if best_score > 0.5:
        logger.debug(f"Best match for '{name}': '{best_match}' (score: {best_score:.3f})")
            
    return best_score
```

>[!info]
>This ensures that names are *matched* against both the **primary name** and **all declared aliases**.

- [[Base Step Specification OutputSpec]]

## Key Methods

### Primary Matching Methods

```python
def calculate_similarity(self, name1: str, name2: str) -> float:
    """Calculate semantic similarity between two names."""

def calculate_similarity_with_aliases(self, name: str, output_spec) -> float:
    """Calculate semantic similarity between a name and an output specification."""
```

### Finding Best Matches

```python
def find_best_matches(self, target_name: str, candidate_names: List[str], 
                     threshold: float = 0.5) -> List[Tuple[str, float]]:
    """
    Find the best matching names from a list of candidates.
    
    Args:
        target_name: Name to match against
        candidate_names: List of candidate names
        threshold: Minimum similarity threshold
        
    Returns:
        List of (name, score) tuples sorted by score (highest first)
    """
```

### Debugging and Explanation

```python
def explain_similarity(self, name1: str, name2: str) -> Dict[str, float]:
    """
    Provide detailed explanation of similarity calculation.
    
    Args:
        name1: First name to compare
        name2: Second name to compare
        
    Returns:
        Dictionary with detailed similarity breakdown
    """
```

## Usage Example

```python
# Create semantic matcher
matcher = SemanticMatcher()

# Calculate similarity between two names
similarity = matcher.calculate_similarity("training_data", "train_dataset")
print(f"Similarity: {similarity:.3f}")  # Output: Similarity: 0.842

# Get detailed explanation
explanation = matcher.explain_similarity("training_data", "train_dataset")
print("Breakdown:")
for metric, score in explanation.items():
    if metric not in ['normalized_names', 'overall_score']:
        print(f"  {metric}: {score:.3f}")

# Find best matches from candidates
candidates = ["model_output", "training_dataset", "validation_data", "test_results"]
best_matches = matcher.find_best_matches("training_data", candidates, threshold=0.7)
print("Best matches:")
for name, score in best_matches:
    print(f"  {name}: {score:.3f}")
```

## Integration with Dependency Resolver

The semantic matcher is a key component of the dependency resolver:

```python
def create_dependency_resolver(registry: Optional[SpecificationRegistry] = None,
                             semantic_matcher: Optional[SemanticMatcher] = None) -> UnifiedDependencyResolver:
    """Create a properly configured dependency resolver."""
    registry = registry or SpecificationRegistry()
    semantic_matcher = semantic_matcher or SemanticMatcher()
    return UnifiedDependencyResolver(registry, semantic_matcher)
```

Within the dependency resolver, it's used to calculate compatibility scores:

```python
# In UnifiedDependencyResolver._calculate_compatibility:
semantic_score = self.semantic_matcher.calculate_similarity_with_aliases(
    dep_spec.logical_name, output_spec
)
score += semantic_score * 0.25  # 25% weight
```

## Benefits of the Design

>[!important]
> The **SemanticMatcher design** offers several key benefits:
> 
> 1. **Robust Matching**: Multiple metrics provide comprehensive similarity assessment
> 2. **Domain Knowledge**: Built-in understanding of ML pipeline terminology
> 3. **Configuration-Free**: No need to manually configure synonyms for each use case
> 4. **Transparent**: Provides detailed explanations of matching decisions
> 5. **Extensible**: Knowledge base can be expanded for specific domains
> 6. **Alias Support**: Handles both primary names and aliases




-----------
##  Recommended Notes

- [[Dependency Resolver for Automatic Pipeline]]
- [[Dependency Resolver System Review]]
- [[Dependency Resolver Design]]
- [[Dependency Resolver Hybrid Design Review]]

- [[Processors ver 2.0]]
- [[Processor CS Chat]]
- [[Processor Tokenizer]]