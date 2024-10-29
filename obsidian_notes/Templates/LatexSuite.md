[
    // Math mode
	{trigger: "mk", replacement: "$$0$", options: "tA"},
	{trigger: "dm", replacement: "$$\n$0\n$$", options: "tAw"},
	{trigger: "beg", replacement: "\\begin{$0}\n$1\n\\end{$0}", options: "mA"},

    // Dashes
	// {trigger: "--", replacement: "–", options: "tA"},
	// {trigger: "–-", replacement: "—", options: "tA"},
	// {trigger: "—-", replacement: "---", options: "tA"},

    // Greek letters
	{trigger: "@a", replacement: "\\alpha", options: "mA"},
	{trigger: "@b", replacement: "\\beta", options: "mA"},
	{trigger: "@g", replacement: "\\gamma", options: "mA"},
	{trigger: "@G", replacement: "\\Gamma", options: "mA"},
	{trigger: "@d", replacement: "\\delta", options: "mA"},
	{trigger: "@D", replacement: "\\Delta", options: "mA"},
	{trigger: "@e", replacement: "\\epsilon", options: "mA"},
	{trigger: ":e", replacement: "\\varepsilon", options: "mA"},
	{trigger: "@z", replacement: "\\zeta", options: "mA"},
	{trigger: "@t", replacement: "\\theta", options: "mA"},
	{trigger: "@T", replacement: "\\Theta", options: "mA"},
	{trigger: ":t", replacement: "\\vartheta", options: "mA"},
	{trigger: "@i", replacement: "\\iota", options: "mA"},
	{trigger: "@k", replacement: "\\kappa", options: "mA"},
	{trigger: "@l", replacement: "\\lambda", options: "mA"},
	{trigger: "@L", replacement: "\\Lambda", options: "mA"},
	{trigger: "@s", replacement: "\\sigma", options: "mA"},
	{trigger: "@S", replacement: "\\Sigma", options: "mA"},
	{trigger: "@u", replacement: "\\upsilon", options: "mA"},
	{trigger: "@U", replacement: "\\Upsilon", options: "mA"},
	{trigger: "@o", replacement: "\\omega", options: "mA"},
	{trigger: "@O", replacement: "\\Omega", options: "mA"},
	{trigger: "ome", replacement: "\\omega", options: "mA"},
	{trigger: "Ome", replacement: "\\Omega", options: "mA"},

    // Text environment
    {trigger: "text", replacement: "\\text{$0}$1", options: "mA"},
    {trigger: "\"", replacement: "\\text{$0}$1", options: "mA"},

    // Basic operations
    {trigger: "sr", replacement: "^{2}", options: "mA"},
	{trigger: "cb", replacement: "^{3}", options: "mA"},
	{trigger: "rd", replacement: "^{$0}$1", options: "mA"},
	{trigger: "_", replacement: "_{$0}$1", options: "mA"},
	{trigger: "sts", replacement: "_\\text{$0}", options: "mA"},
	{trigger: "sq", replacement: "\\sqrt{ $0 }$1", options: "mA"},
	{trigger: "//", replacement: "\\frac{$0}{$1}$2", options: "mA"},
	{trigger: "ee", replacement: "e^{ $0 }$1", options: "mA"},
    {trigger: "invs", replacement: "^{-1}", options: "mA"},
    {trigger: /([A-Za-z])(\d)/, replacement: "[[0]]_{[[1]]}", options: "rmA", description: "Auto letter subscript", priority: -1},

    {trigger: /([^\\])(exp|log|ln)/, replacement: "[[0]]\\[[1]]", options: "rmA"},
    {trigger: "conj", replacement: "^{*}", options: "mA"},
    {trigger: "Re", replacement: "\\mathrm{Re}", options: "mA"},
	{trigger: "Im", replacement: "\\mathrm{Im}", options: "mA"},
    {trigger: "bf", replacement: "\\mathbf{$0}", options: "mA"},
	{trigger: "rm", replacement: "\\mathrm{$0}$1", options: "mA"},

    // Linear algebra
    {trigger: /([^\\])(det)/, replacement: "[[0]]\\[[1]]", options: "rmA"},
    {trigger: "trace", replacement: "\\mathrm{Tr}", options: "mA"},

    // More operations
	{trigger: "([a-zA-Z])hat", replacement: "\\hat{[[0]]}", options: "rmA"},
    {trigger: "([a-zA-Z])bar", replacement: "\\bar{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])dot", replacement: "\\dot{[[0]]}", options: "rmA", priority: -1},
	{trigger: "([a-zA-Z])ddot", replacement: "\\ddot{[[0]]}", options: "rmA", priority: 1},
	{trigger: "([a-zA-Z])tilde", replacement: "\\tilde{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])und", replacement: "\\underline{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])vec", replacement: "\\vec{[[0]]}", options: "rmA"},
    {trigger: "([a-zA-Z]),\\.", replacement: "\\mathbf{[[0]]}", options: "rmA"},
	{trigger: "([a-zA-Z])\\.,", replacement: "\\mathbf{[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}),\\.", replacement: "\\boldsymbol{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK})\\.,", replacement: "\\boldsymbol{\\[[0]]}", options: "rmA"},

	{trigger: "hat", replacement: "\\hat{$0}$1", options: "mA"},
    {trigger: "bar", replacement: "\\bar{$0}$1", options: "mA"},
	{trigger: "dot", replacement: "\\dot{$0}$1", options: "mA", priority: -1},
	{trigger: "ddot", replacement: "\\ddot{$0}$1", options: "mA"},
	{trigger: "cdot", replacement: "\\cdot", options: "mA"},
	{trigger: "tilde", replacement: "\\tilde{$0}$1", options: "mA"},
	{trigger: "und", replacement: "\\underline{$0}$1", options: "mA"},
	{trigger: "vec", replacement: "\\vec{$0}$1", options: "mA"},

    // More auto letter subscript
    {trigger: /([A-Za-z])_(\d\d)/, replacement: "[[0]]_{[[1]]}", options: "rmA"},
	{trigger: /\\hat{([A-Za-z])}(\d)/, replacement: "\\hat{[[0]]}_{[[1]]}", options: "rmA"},
	{trigger: /\\vec{([A-Za-z])}(\d)/, replacement: "\\vec{[[0]]}_{[[1]]}", options: "rmA"},
	{trigger: /\\mathbf{([A-Za-z])}(\d)/, replacement: "\\mathbf{[[0]]}_{[[1]]}", options: "rmA"},

    {trigger: "xnn", replacement: "x_{n}", options: "mA"},
	{trigger: "xii", replacement: "x_{i}", options: "mA"},
	{trigger: "xjj", replacement: "x_{j}", options: "mA"},
	{trigger: "xp1", replacement: "x_{n+1}", options: "mA"},
	{trigger: "ynn", replacement: "y_{n}", options: "mA"},
	{trigger: "yii", replacement: "y_{i}", options: "mA"},
	{trigger: "yjj", replacement: "y_{j}", options: "mA"},

    // Symbols
    {trigger: "ooo", replacement: "\\infty", options: "mA"},
	{trigger: "sum", replacement: "\\sum", options: "mA"},
	{trigger: "prod", replacement: "\\prod", options: "mA"},
	{trigger: "\\sum", replacement: "\\sum_{${0:i}=${1:1}}^{${2:N}} $3", options: "m"},
	{trigger: "\\prod", replacement: "\\prod_{${0:i}=${1:1}}^{${2:N}} $3", options: "m"},
    {trigger: "lim", replacement: "\\lim_{ ${0:n} \\to ${1:\\infty} } $2", options: "mA"},
    {trigger: "+-", replacement: "\\pm", options: "mA"},
	{trigger: "-+", replacement: "\\mp", options: "mA"},
    {trigger: "...", replacement: "\\dots", options: "mA"},
    {trigger: "nabl", replacement: "\\nabla", options: "mA"},
	{trigger: "del", replacement: "\\nabla", options: "mA"},
    {trigger: "xx", replacement: "\\times", options: "mA"},
    {trigger: "**", replacement: "\\cdot", options: "mA"},
    {trigger: "para", replacement: "\\parallel", options: "mA"},

	{trigger: "===", replacement: "\\equiv", options: "mA"},
    {trigger: "!=", replacement: "\\neq", options: "mA"},
	{trigger: ">=", replacement: "\\geq", options: "mA"},
	{trigger: "<=", replacement: "\\leq", options: "mA"},
	{trigger: ">>", replacement: "\\gg", options: "mA"},
	{trigger: "<<", replacement: "\\ll", options: "mA"},
	{trigger: "simm", replacement: "\\sim", options: "mA"},
	{trigger: "sim=", replacement: "\\simeq", options: "mA"},
    {trigger: "prop", replacement: "\\propto", options: "mA"},


    {trigger: "<->", replacement: "\\leftrightarrow ", options: "mA"},
	{trigger: "->", replacement: "\\to", options: "mA"},
	{trigger: "!>", replacement: "\\mapsto", options: "mA"},
    {trigger: "=>", replacement: "\\implies", options: "mA"},
	{trigger: "=<", replacement: "\\impliedby", options: "mA"},

	{trigger: "and", replacement: "\\cap", options: "mA"},
	{trigger: "orr", replacement: "\\cup", options: "mA"},
	{trigger: "inn", replacement: "\\in", options: "mA"},
	{trigger: "notin", replacement: "\\not\\in", options: "mA"},
    {trigger: "\\\\\\", replacement: "\\setminus", options: "mA"},
    {trigger: "sub=", replacement: "\\subseteq", options: "mA"},
    {trigger: "sup=", replacement: "\\supseteq", options: "mA"},
	{trigger: "eset", replacement: "\\emptyset", options: "mA"},
	{trigger: "set", replacement: "\\{ $0 \\}$1", options: "mA"},
	{trigger: "e\\xi sts", replacement: "\\exists", options: "mA", priority: 1},

	{trigger: "LL", replacement: "\\mathcal{L}", options: "mA"},
	{trigger: "HH", replacement: "\\mathcal{H}", options: "mA"},
	{trigger: "CC", replacement: "\\mathbb{C}", options: "mA"},
	{trigger: "RR", replacement: "\\mathbb{R}", options: "mA"},
	{trigger: "ZZ", replacement: "\\mathbb{Z}", options: "mA"},
	{trigger: "NN", replacement: "\\mathbb{N}", options: "mA"},
    
    // Customized symbols
    {trigger: "cA", replacement: "\\mathcal{A}", options: "mA"},
    {trigger: "cB", replacement: "\\mathcal{B}", options: "mA"},
    {trigger: "cC", replacement: "\\mathcal{C}", options: "mA"},
    {trigger: "cD", replacement: "\\mathcal{D}", options: "mA"},
    {trigger: "cE", replacement: "\\mathcal{E}", options: "mA"},
    {trigger: "cF", replacement: "\\mathcal{F}", options: "mA"},
    {trigger: "cG", replacement: "\\mathcal{G}", options: "mA"},
    {trigger: "cH", replacement: "\\mathcal{H}", options: "mA"},
    {trigger: "cI", replacement: "\\mathcal{I}", options: "mA"},
    {trigger: "cJ", replacement: "\\mathcal{J}", options: "mA"},
    {trigger: "cK", replacement: "\\mathcal{K}", options: "mA"},
    {trigger: "cL", replacement: "\\mathcal{L}", options: "mA"},
    {trigger: "cM", replacement: "\\mathcal{M}", options: "mA"},
    {trigger: "cN", replacement: "\\mathcal{N}", options: "mA"},
    {trigger: "cO", replacement: "\\mathcal{O}", options: "mA"},
    {trigger: "cP", replacement: "\\mathcal{P}", options: "mA"},
    {trigger: "cQ", replacement: "\\mathcal{Q}", options: "mA"},
    {trigger: "cR", replacement: "\\mathcal{R}", options: "mA"},
    {trigger: "cS", replacement: "\\mathcal{S}", options: "mA"},
    {trigger: "cT", replacement: "\\mathcal{T}", options: "mA"},
    {trigger: "cU", replacement: "\\mathcal{U}", options: "mA"},
    {trigger: "cV", replacement: "\\mathcal{V}", options: "mA"},
    {trigger: "cW", replacement: "\\mathcal{W}", options: "mA"},
    {trigger: "cX", replacement: "\\mathcal{X}", options: "mA"},
    {trigger: "cY", replacement: "\\mathcal{Y}", options: "mA"},
    {trigger: "cZ", replacement: "\\mathcal{Z}", options: "mA"},

    {trigger: "bA", replacement: "\\mathbb{A}", options: "mA"},
    {trigger: "bB", replacement: "\\mathbb{B}", options: "mA"},
    {trigger: "bC", replacement: "\\mathbb{C}", options: "mA"},
    {trigger: "bD", replacement: "\\mathbb{D}", options: "mA"},
    {trigger: "bE", replacement: "\\mathbb{E}", options: "mA"},
    {trigger: "bF", replacement: "\\mathbb{F}", options: "mA"},
    {trigger: "bG", replacement: "\\mathbb{G}", options: "mA"},
    {trigger: "bH", replacement: "\\mathbb{H}", options: "mA"},
    {trigger: "bI", replacement: "\\mathbb{I}", options: "mA"},
    {trigger: "bJ", replacement: "\\mathbb{J}", options: "mA"},
    {trigger: "bK", replacement: "\\mathbb{K}", options: "mA"},
    {trigger: "bL", replacement: "\\mathbb{L}", options: "mA"},
    {trigger: "bM", replacement: "\\mathbb{M}", options: "mA"},
    {trigger: "bN", replacement: "\\mathbb{N}", options: "mA"},
    {trigger: "bO", replacement: "\\mathbb{O}", options: "mA"},
    {trigger: "bP", replacement: "\\mathbb{P}", options: "mA"},
    {trigger: "bQ", replacement: "\\mathbb{Q}", options: "mA"},
    {trigger: "bR", replacement: "\\mathbb{R}", options: "mA"},
    {trigger: "bS", replacement: "\\mathbb{S}", options: "mA"},
    {trigger: "bT", replacement: "\\mathbb{T}", options: "mA"},
    {trigger: "bU", replacement: "\\mathbb{U}", options: "mA"},
    {trigger: "bV", replacement: "\\mathbb{V}", options: "mA"},
    {trigger: "bW", replacement: "\\mathbb{W}", options: "mA"},
    {trigger: "bX", replacement: "\\mathbb{X}", options: "mA"},
    {trigger: "bY", replacement: "\\mathbb{Y}", options: "mA"},
    {trigger: "bZ", replacement: "\\mathbb{Z}", options: "mA"},

    {trigger: "scA", replacement: "\\mathscr{A}", options: "mA"},
    {trigger: "scB", replacement: "\\mathscr{B}", options: "mA"},
    {trigger: "scC", replacement: "\\mathscr{C}", options: "mA"},
    {trigger: "scD", replacement: "\\mathscr{D}", options: "mA"},
    {trigger: "scE", replacement: "\\mathscr{E}", options: "mA"},
    {trigger: "scF", replacement: "\\mathscr{F}", options: "mA"},
    {trigger: "scG", replacement: "\\mathscr{G}", options: "mA"},
    {trigger: "scH", replacement: "\\mathscr{H}", options: "mA"},
    {trigger: "scI", replacement: "\\mathscr{I}", options: "mA"},
    {trigger: "scJ", replacement: "\\mathscr{J}", options: "mA"},
    {trigger: "scK", replacement: "\\mathscr{K}", options: "mA"},
    {trigger: "scL", replacement: "\\mathscr{L}", options: "mA"},
    {trigger: "scM", replacement: "\\mathscr{M}", options: "mA"},
    {trigger: "scN", replacement: "\\mathscr{N}", options: "mA"},
    {trigger: "scO", replacement: "\\mathscr{O}", options: "mA"},
    {trigger: "scP", replacement: "\\mathscr{P}", options: "mA"},
    {trigger: "scQ", replacement: "\\mathscr{Q}", options: "mA"},
    {trigger: "scR", replacement: "\\mathscr{R}", options: "mA"},
    {trigger: "scS", replacement: "\\mathscr{S}", options: "mA"},
    {trigger: "scT", replacement: "\\mathscr{T}", options: "mA"},
    {trigger: "scU", replacement: "\\mathscr{U}", options: "mA"},
    {trigger: "scV", replacement: "\\mathscr{V}", options: "mA"},
    {trigger: "scW", replacement: "\\mathscr{W}", options: "mA"},
    {trigger: "scX", replacement: "\\mathscr{X}", options: "mA"},
    {trigger: "scY", replacement: "\\mathscr{Y}", options: "mA"},
    {trigger: "scZ", replacement: "\\mathscr{Z}", options: "mA"},
    
    {trigger: "frA", replacement: "\\mathfrak{A}", options: "mA"},
    {trigger: "frG", replacement: "\\mathfrak{G}", options: "mA"},
    {trigger: "frM", replacement: "\\mathfrak{M}", options: "mA"},
    {trigger: "frP", replacement: "\\mathfrak{P}", options: "mA"},
    {trigger: "frR", replacement: "\\mathfrak{R}", options: "mA"},
    {trigger: "frS", replacement: "\\mathfrak{S}", options: "mA"},
    {trigger: "frX", replacement: "\\mathfrak{X}", options: "mA"},

    {trigger: "mb", replacement: "\\boldsymbol{$0}", options: "mA"},
    {trigger: "xdx", replacement: "\\,{$0}\\ldots{$0}\\,", options: "mA"},
    {trigger: "paren", replacement: "\\left($0\\right)", options: "mA"},
    {trigger: "kldiv", replacement: "\\mathbb{KL}\\left( $0 \\left\\|\\right. $1 \\right)", options: "mA"},
    {trigger: "div", replacement: "\\mathbb{D}\\left( $0 \\left\\|\\right. $1 \\right)", options: "mA"},
    {trigger: "<>", replacement: "\\left\\langle  $0\\,,\\, $1   \\right\\rangle", options: "mA"},
    {trigger: "vect", replacement: "\text{vec}\\left( $0 \\right)", options: "mA"},
    {trigger: "diag", replacement: "\text{diag}\\left( $0 \\right)", options: "mA"},
    {trigger: "pmean", replacement: "\\mathbb{E}_{ ${0:p} }\\left[  ${1:X} \\right]", options: "m"},
    {trigger: "se-", replacement: "\\setminus", options: "mA"},
    {trigger: "subs-", replacement: "\\subset", options: "mA"},
    {trigger: "circ", replacement: "\\circ", options: "m"},
    
    // Handle spaces and backslashes

    // Snippet variables can be used as shortcuts when writing snippets.
    // For example, ${GREEK} below is shorthand for "alpha|beta|gamma|Gamma|delta|..."
    // You can edit snippet variables under the Advanced snippet settings section.

	{trigger: "([^\\\\])(${GREEK})", replacement: "[[0]]\\[[1]]", options: "rmA", description: "Add backslash before Greek letters"},
	{trigger: "([^\\\\])(${SYMBOL})", replacement: "[[0]]\\[[1]]", options: "rmA", description: "Add backslash before symbols"},

    // Insert space after Greek letters and symbols
	{trigger: "\\\\(${GREEK}|${SYMBOL}|${MORE_SYMBOLS})([A-Za-z])", replacement: "\\[[0]] [[1]]", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) sr", replacement: "\\[[0]]^{2}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) cb", replacement: "\\[[0]]^{3}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) rd", replacement: "\\[[0]]^{$0}$1", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) hat", replacement: "\\hat{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) dot", replacement: "\\dot{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) bar", replacement: "\\bar{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) vec", replacement: "\\vec{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) tilde", replacement: "\\tilde{\\[[0]]}", options: "rmA"},
	{trigger: "\\\\(${GREEK}|${SYMBOL}) und", replacement: "\\underline{\\[[0]]}", options: "rmA"},


    // Derivatives and integrals
    {trigger: "par", replacement: "\\frac{ \\partial ${0:y} }{ \\partial ${1:x} } $2", options: "m"},
    {trigger: /pa([A-Za-z])([A-Za-z])/, replacement: "\\frac{ \\partial [[0]] }{ \\partial [[1]] } ", options: "rm"},
    {trigger: "ddt", replacement: "\\frac{d}{dt} ", options: "mA"},

    {trigger: /([^\\])int/, replacement: "[[0]]\\int", options: "mA", priority: -1},
    {trigger: "\\int", replacement: "\\int $0 \\, d${1:x} $2", options: "m"},
    {trigger: "dint", replacement: "\\int_{${0:0}}^{${1:1}} $2 \\, d${3:x} $4", options: "mA"},
    {trigger: "oint", replacement: "\\oint", options: "mA"},
	{trigger: "iint", replacement: "\\iint", options: "mA"},
    {trigger: "iiint", replacement: "\\iiint", options: "mA"},
    {trigger: "oinf", replacement: "\\int_{0}^{\\infty} $0 \\, d${1:x} $2", options: "mA"},
	{trigger: "infi", replacement: "\\int_{-\\infty}^{\\infty} $0 \\, d${1:x} $2", options: "mA"},


    // Trigonometry
    {trigger: /([^\\])(arcsin|sin|arccos|cos|arctan|tan|csc|sec|cot)/, replacement: "[[0]]\\[[1]]", options: "rmA", description: "Add backslash before trig funcs"},

    {trigger: /\\(arcsin|sin|arccos|cos|arctan|tan|csc|sec|cot)([A-Za-gi-z])/,
     replacement: "\\[[0]] [[1]]", options: "rmA",
     description: "Add space after trig funcs. Skips letter h to allow sinh, cosh, etc."},

    {trigger: /\\(sinh|cosh|tanh|coth)([A-Za-z])/,
     replacement: "\\[[0]] [[1]]", options: "rmA",
     description: "Add space after hyperbolic trig funcs"},


    // Visual operations
	{trigger: "U", replacement: "\\underbrace{ ${VISUAL} }_{ $0 }", options: "mA"},
	{trigger: "O", replacement: "\\overbrace{ ${VISUAL} }^{ $0 }", options: "mA"},
	{trigger: "B", replacement: "\\underset{ $0 }{ ${VISUAL} }", options: "mA"},
	{trigger: "C", replacement: "\\cancel{ ${VISUAL} }", options: "mA"},
	{trigger: "K", replacement: "\\cancelto{ $0 }{ ${VISUAL} }", options: "mA"},
	{trigger: "S", replacement: "\\sqrt{ ${VISUAL} }", options: "mA"},


    // Physics
	{trigger: "kbt", replacement: "k_{B}T", options: "mA"},
	{trigger: "msun", replacement: "M_{\\odot}", options: "mA"},

    // Quantum mechanics
    {trigger: "dag", replacement: "^{\\dagger}", options: "mA"},
	{trigger: "o+", replacement: "\\oplus ", options: "mA"},
	{trigger: "ox", replacement: "\\otimes ", options: "mA"},
    {trigger: "bra", replacement: "\\bra{$0} $1", options: "mA"},
	{trigger: "ket", replacement: "\\ket{$0} $1", options: "mA"},
	{trigger: "brk", replacement: "\\braket{ $0 | $1 } $2", options: "mA"},
    {trigger: "outer", replacement: "\\ket{${0:\\psi}} \\bra{${0:\\psi}} $1", options: "mA"},

    // Chemistry
	{trigger: "pu", replacement: "\\pu{ $0 }", options: "mA"},
	{trigger: "cee", replacement: "\\ce{ $0 }", options: "mA"},
	{trigger: "he4", replacement: "{}^{4}_{2}He ", options: "mA"},
	{trigger: "he3", replacement: "{}^{3}_{2}He ", options: "mA"},
	{trigger: "iso", replacement: "{}^{${0:4}}_{${1:2}}${2:He}", options: "mA"},


    // Environments
	{trigger: "pmat", replacement: "\\begin{pmatrix}\n$0\n\\end{pmatrix}", options: "MA"},
	{trigger: "bmat", replacement: "\\begin{bmatrix}\n$0\n\\end{bmatrix}", options: "MA"},
	{trigger: "Bmat", replacement: "\\begin{Bmatrix}\n$0\n\\end{Bmatrix}", options: "MA"},
	{trigger: "vmat", replacement: "\\begin{vmatrix}\n$0\n\\end{vmatrix}", options: "MA"},
	{trigger: "Vmat", replacement: "\\begin{Vmatrix}\n$0\n\\end{Vmatrix}", options: "MA"},
	{trigger: "matrix", replacement: "\\begin{matrix}\n$0\n\\end{matrix}", options: "MA"},

	{trigger: "pmat", replacement: "\\begin{pmatrix}$0\\end{pmatrix}", options: "nA"},
	{trigger: "bmat", replacement: "\\begin{bmatrix}$0\\end{bmatrix}", options: "nA"},
	{trigger: "Bmat", replacement: "\\begin{Bmatrix}$0\\end{Bmatrix}", options: "nA"},
	{trigger: "vmat", replacement: "\\begin{vmatrix}$0\\end{vmatrix}", options: "nA"},
	{trigger: "Vmat", replacement: "\\begin{Vmatrix}$0\\end{Vmatrix}", options: "nA"},
	{trigger: "matrix", replacement: "\\begin{matrix}$0\\end{matrix}", options: "nA"},

	{trigger: "cases", replacement: "\\begin{cases}\n$0\n\\end{cases}", options: "mA"},
	{trigger: "align", replacement: "\\begin{align}\n$0\n\\end{align}", options: "mA"},
	{trigger: "array", replacement: "\\begin{array}\n$0\n\\end{array}", options: "mA"},


    // Brackets
	{trigger: "avg", replacement: "\\langle $0 \\rangle $1", options: "mA"},
	{trigger: "norm", replacement: "\\lvert $0 \\rvert $1", options: "mA", priority: 1},
	{trigger: "Norm", replacement: "\\lVert $0 \\rVert $1", options: "mA", priority: 1},
	{trigger: "ceil", replacement: "\\lceil $0 \\rceil $1", options: "mA"},
	{trigger: "floor", replacement: "\\lfloor $0 \\rfloor $1", options: "mA"},
	{trigger: "mod", replacement: "|$0|$1", options: "mA"},
	{trigger: "(", replacement: "(${VISUAL})", options: "mA"},
	{trigger: "[", replacement: "[${VISUAL}]", options: "mA"},
	{trigger: "{", replacement: "{${VISUAL}}", options: "mA"},
	{trigger: "(", replacement: "($0)$1", options: "mA"},
	{trigger: "{", replacement: "{$0}$1", options: "mA"},
	{trigger: "[", replacement: "[$0]$1", options: "mA"},
	{trigger: "lr(", replacement: "\\left( $0 \\right) $1", options: "mA"},
	{trigger: "lr{", replacement: "\\left\\{ $0 \\right\\} $1", options: "mA"},
	{trigger: "lr[", replacement: "\\left[ $0 \\right] $1", options: "mA"},
	{trigger: "lr|", replacement: "\\left| $0 \\right| $1", options: "mA"},
	{trigger: "lra", replacement: "\\left< $0 \\right> $1", options: "mA"},


    // Misc

    // Automatically convert standalone letters in text to math (except a, A, I).
    // (Un-comment to enable)
    // {trigger: /([^'])\b([B-HJ-Zb-z])\b([\n\s.,?!:'])/, replacement: "[[0]]$[[1]]$[[2]]", options: "tA"},

    // Automatically convert Greek letters in text to math.
    // {trigger: "(${GREEK})([\\n\\s.,?!:'])", replacement: "$\\[[0]]$[[1]]", options: "rtAw"},

    // Automatically convert text of the form "x=2" and "x=n+1" to math.
    // {trigger: /([A-Za-z]=\d+)([\n\s.,?!:'])/, replacement: "$[[0]]$[[1]]", options: "rtAw"},
    // {trigger: /([A-Za-z]=[A-Za-z][+-]\d+)([\n\s.,?!:'])/, replacement: "$[[0]]$[[1]]", options: "tAw"},


    // Snippet replacements can have placeholders.
	{trigger: "tayl", replacement: "${0:f}(${1:x} + ${2:h}) = ${0:f}(${1:x}) + ${0:f}'(${1:x})${2:h} + ${0:f}''(${1:x}) \\frac{${2:h}^{2}}{2!} + \\dots$3", options: "mA", description: "Taylor expansion"},

    // Snippet replacements can also be JavaScript functions.
    // See the documentation for more information.
	{trigger: /iden(\d)/, replacement: (match) => {
		const n = match[1];

		let arr = [];
		for (let j = 0; j < n; j++) {
			arr[j] = [];
			for (let i = 0; i < n; i++) {
				arr[j][i] = (i === j) ? 1 : 0;
			}
		}

		let output = arr.map(el => el.join(" & ")).join(" \\\\\n");
		output = `\\begin{pmatrix}\n${output}\n\\end{pmatrix}`;
		return output;
	}, options: "mA", description: "N x N identity matrix"},
]
