# C-minus-Compiler  
A compiler for a reduced version of the C language. Outputs mips instructions to a file, which can then be run.

The Grammar this compiler is based on is below. This grammar below, however, is not complete in identifying the grammar that describes the syntax of this compiler. More specifically, this compiler does more than listed below.  
### BNF Grammar for C-Minus

1. program → declaration-list
2. declaration-list → declaration-list declaration | declaration
3. declaration → var-declaration | fun-declaration
4. var-declaration → type-specifier ID ; | type-specifier ID [ NUM ] ;
5. type-specifier → int | void
6. fun-declaration → type-specifier ID ( params ) compound-stmt
7. params → param-list | void
8. param-list → param-list , param | param
9. param → type-specifier ID | type-specifier ID [ ]
10. compound-stmt → { local-declarations statement-list }
11. local-declarations → local-declarations var-declarations | empty
12. statement-list → statement-list statement | empty
13. statement → expression-stmt | compound-stmt | selection-stmt | iteration-stmt | return-stmt
14. expression-stmt → expression ; | ;
15. selection-stmt → if ( expression ) statement | if ( expression ) statement else statement
16. iteration-stmt → while ( expression ) statement
17. return-stmt → return ; | return expression ;
18. expression → var = expression | simple-expression
19. var → ID | ID [ expression ]
20. simple-expression → additive-expression relop additive-expression | additive-expression
21. relop → <= | < | > | >= | == | !=
22. additive-expression → additive-expression addop term | term
23. addop → + | -
24. term → term mulop factor | factor
25. mulop → * | /
26. factor → ( expression ) | var | call | NUM
27. call → ID ( args )
28. args → arg-list | empty
29. arg-list → arg-list , expression | expression 
