# compile

lex text.l
cc lex.yy.c
./a.out

# lex program to count number of words
%{ 
#include<stdio.h> 
#include<string.h> 
int i = 0; 
%} 
%% 
([a-zA-Z0-9])* {i++;} 
"\n" {printf("%d\n", i); i = 0;} 
%% 
int yywrap(void){} 
int main() 
{ 
	// The function that starts the analysis 
	yylex(); 
	return 0; 
} 

# token seperation
%{

%}
%%
[0-9]+[.][0-9]+ printf("%s is a floating point number\n",yytext);
int|float|char|double|void printf("%s is a datatype\n",yytext);
[0-9]+ printf("%s is an integer number\n",yytext);
[a-z]+[()] printf("%s is a function\n",yytext);
[a-z]+ printf("%s is an identifier\n",yytext);
[+=*/-] printf("%s is an operator\n",yytext);
; printf("%s is an delimiter\n",yytext);
, printf("%s is a separator\n",yytext);
[#][a-z\.h]+ printf("%s is a preprocessor\n",yytext);
%%
int yywrap(void)
{
        return 1;
}
int main()
{
  // reads input from a file named test.c rather than terminal
  freopen("text.c", "r", stdin);
        yylex();
        return 0;
}



text.c
int main()
{
int a = 2;
float b = 3;  
return 0;}

# deterministic finite automata

no_states = int(input())
transition_table = {}
index = {}
for i in range(no_states):
  x,y,z = input().split()
  transition_table[x] = [y,z]
  index[i] = x

  3
A B C
C B A
B B A

in_str = input()
state = 0
for i in in_str:
  if i == 'a':
    state = (list(index.keys())[list(index.values()).index(transition_table[index[state]][0])])
  else:
    state = (list(index.keys())[list(index.values()).index(transition_table[index[state]][1])])
if state == no_states-1:
  print(True)
else:
  print(False)

aabb
False

# yacc 

%{
#include <math.h>
#include <stdio.h>
#include <ctype.h>
#define YYSTYPE double
%}
%%
input :
    | input line
    ;
line : '\n'
    | expr '\n' { printf("Result is %g", $1); }
    ;
expr : expr '+' term { $$ = $1 + $3; }
     | expr '-' term { $$ = $1 - $3; }
     | term { $$ = $1; }
     ;
term : term '*' factor { $$ = $1 * $3; }
     | term '/' factor { $$ = $1 / $3; }
     | factor { $$ = $1; }
     ;
factor : NUM { $$ = $1; }
       ;
NUM : digit { $$ = $1; }
    | NUM digit { $$ = $1 * 10 + $2; }
    ;
digit : '0' { $$ = 0; }
      | '1' { $$ = 1; }
      | '2' { $$ = 2; }
      | '3' { $$ = 3; }
      | '4' { $$ = 4; }
      | '5' { $$ = 5; }
      | '6' { $$ = 6; }
      | '7' { $$ = 7; }
      | '8' { $$ = 8; }
      | '9' { $$ = 9; }
      ;
%%
int yylex() {
    return getchar();
}
int main() {
    return yyparse();
}
void yyerror(char *s) {
    printf("%s", s);
}

yacc program.c
gcc y.tab.c
./a.out

# lex -word starting with vowels

%{
#include <stdio.h>
%}
VOWEL [aeiouAEIOU]
WORD [a-zA-Z]+

%%
^({VOWEL}{WORD})    printf("Word starting with a vowel: %s\n", yytext);
.|\n                
%%
int yywrap() {
    return 0;
}
int main() {
    yylex();
    return 0;
}

# operators

%{
#include <stdio.h>
%}

OPERATOR [+|\-|*|/|=|>|<|%|&|!|^|~|\?|:|\|]
CONSONANT [bcdfghjklmnpqrstvwxyzBCDFGHJKLMNPQRSTVWXYZ]

%%
{OPERATOR}      printf("Operator: %s\n", yytext);
{CONSONANT}+    printf("Consonant: %s\n", yytext);
.|\n            // skip other characters
%%

int yywrap() {
    return 0;
}

int main() {
    yylex();
    return 0;
}

# odd or even
%{
#include <stdio.h>
%}
DIGIT [0-9]
%%
{DIGIT}+ {
    int num = atoi(yytext);
    if (num % 2 == 0) {
        printf("%d is even\n", num);
    } else {
        printf("%d is odd\n", num);
    }
}
.|\n    // skip other characters
%%
int yywrap() {
    return 0;
}
int main() {
    yylex();
    return 0;
}


