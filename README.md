%{
int word_count = 0;
%}

%%
[a-zA-Z]+ { word_count++; }
.|\n     { /* Ignore other characters and newlines */ }
%%

int main() {
    yylex();
    printf("Total number of words: %d\n", word_count);
    return 0;
}
