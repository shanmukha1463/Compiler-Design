# Implimenting a simple calculator using yacc tool
The calculator performs arithmatic operations on float numbers using BODMAS rule and parenthesis are given highest priority.

This approach gives plus greater priority/precedence than minus. 
If we want to give plus and minus same precedence and follow left to right associativity, 
then use %left in yacc and use single production for both plus and minus.

For some reason, to use this grammar for left to right associative calculation, use parentheses ;P

Same is applicable for division and multiplication. 

- Note: --report=all --report-file=logfile arguments produce a report mentioning all the states, items and transitions.

### Grammar: (compilation)

```bash
flex grammar.lex
yacc -d grammar.y --report=all --report-file=logfile
gcc y.tab.c
```
 
### Inputs: 

```bash
./a.out input1.txt              # valid syntax
./a.out input2.txt              # valid syntax
./a.out input3.txt              # syntax error
./a.out input4.txt              # valid syntax but gives different answer than a regular calculator (BODMAS vs left to right associativity)
```