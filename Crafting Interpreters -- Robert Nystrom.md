### Steps in compilation/interpretation
Scanning/Lexical Analysis (lexing) -> Parsing -> Static Analysis

### Scanning/Lexical Analysis
So, a scanner/lexer takes in a 'Stream' of characters & CHUNKS them into things akin to words. I feel that this is important to emphasize (and visualise). These 'words' are what we call ___tokens___. These tokens can be single characters like '(' and ',' or several chars long

Some characters in a source file don't mean anything, like whitespace (sometimes) or comments (all the times, expect docstrings - but those aren't compiled to machine code)


### Parsing
This is the next step. Here, our syntax gets a [__Grammer__](obsidian://open?vault=My%20Courses&file=Theory%20of%20Computation)-the ability to compose larger expressions. Like a sentence diagram or tree (modern guys call them Abstract Syntax Trees. Sound family me thinks). The Keyword of PL though, are 'keywords', which they have a lot less of as compared to natural languages

So, the parser takes a flat sequence of characters and builds that into a syntax tree that mirrors the nested nature of grammar. ASTs are also called parse trees (but that's old school)

Parsing has a rich history in AI (Symbolic) and a lot of the advanced techniques we use were borne out of Computer scientists and mathematicians trying to get computers to understand messy human languages


##### Note:
So far, for the above two stages, the implementation across PLs are pretty standard and rarely deviate, especially if the PLs are modern

### Static Analysis
This is where it begins to get serious!!!

This bit if fun. So lets get into it

Static analysis is  basically were meaning is given to code. While scanning in responsible for identifying the tokens, and parsing for organising those tokens into tree-like expression trees, Static Analysis is were those expressions are given semantic meaning.

This is embodied in the two core actions that take place in this step: ___Binding___ and ___Resolution___.

__Binding__ is basically


