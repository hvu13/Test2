# Test2
### a 
Following are rules for recognizing all lexemes as their proper token:
1)  The compiler first reads the source code which is in the form of High level or any level language.
2) The language analyzer sort the source code into lexemes, which are the grammar of the machine the valid lexemes are tokens.
3) Then the lexical analyzer dissociates the tokens and validates them after removing white space called proper tokens.
Integer token code:
{
int  i = 2;   //source code 
}
Here in the given code, 
→ The number of identifiers is i (identifier).
→ the operator is equals (=).
→ The constant is number(2).
→The keyword is int.
→ The only punctuation is (;).
Here, the number of tokens is 5.
 
Regular Expression- 
The only valid syntax of any particular language is read by a lexical analyzer that follows the above rules such expressions called Regular Expressions in the given code have the Regular Expression.
Regular Grammar or Finite automata-
The Regular Expression follows certain programming principles having finite sets of strings, variables, etc the grammar it follows is termed Regular Grammar or Finite automata. 
 
### b & c & d
<blockquote>
<p>Expressions:</p>
<p>E → E + T | E - T | T</p>
<p>T → T * F | T / F | F</p>
<p>F → (E) | id</p>
<p>id → a | b | c | d | ... | z</p>
</blockquote>
 
<blockquote>
<p>Statements:</p>
<p>S → if E then S | while E do S | begin opt_stmts end</p>
<p>opt_stmts → stmts | ε</p>
<p>stmts → stmt ; stmts | stmt</p>
<p>stmt → assign_stmt | loop_stmt | selection_stmt</p>
<p>assign_stmt → id := E</p>
<p>loop_stmt → for id := E to E do S</p>
<p>selection_stmt → if E then S</p>
</blockquote>
 
<blockquote>
<p>Declarations:</p>
<p>D → int id | float id | bool id | char id</p>
</blockquote>
 
<blockquote>
<p>Rules of Inference</p>
<p>E → E + T | E - T | T</p>
<p>T → T * F | T / F | F</p>
<p>F → (E) | id</p>
<p>id → a | b | c | d | ... | z</p>
<p>S → if E then S | while E do S | begin opt_stmts end</p>
<p>opt_stmts → stmts | ε</p>
<p>stmts → stmt ; stmts | stmt</p>
<p>stmt → assign_stmt | loop_stmt | selection_stmt</p>
<p>assign_stmt → id := E</p>
<p>loop_stmt → for id := E to E do S</p>
<p>selection_stmt → if E then S</p>
<p>D → int id | float id | bool id | char id</p>
</blockquote>
 
LL(1) Grammar
 
E  → TE'

E' → +TE' | -TE' | ε

T  → FT'

T' → *FT' | /FT' | ε

F  → (E) | id

id → a | b | c | d | ... | z

S  → ifEthenS | whileEdoS | beginOSend

OS → OS;S | S

S  → assign_stmt | loop_stmt | selection_stmt

assign_stmt → id:=E

loop_stmt → forid:=EtoEdoS

selection_stmt  → ifEthenS

D  → intid | floatid | boolid | charid

1) The first step is to declare the variables that will be used in the program. These include the variable "E" which will be used to store the value of the expression, the variable "T" which will be used to store the value of the term, the variable "F" which will be used to store the value of the factor, and the variable "id" which will be used to store the value of the identifier.
2) The next step is to define the production rules for the operators and operands, loops, variable declaration, and selection statements.
3) The next step is to enforce a non-PEMDAS (BODMAS) order of operation. This means that the operators must be evaluated in a different order than what is typically used in mathematics.
4) The next step is to make sure that the keywords are unique and that they do not use the words "while", "for", "do", "if", "int", "short", "long", or "i".
5) The next step is to clearly state the structure of the language with production rules.
6) The next step is to show whether every rule set in the language conforms to the standard of an LL grammar.
7) The last step is to make sure that the grammar is not ambiguous.
 
Also
I would use a grammar similar to the one below (I've written it in ANTLR):

<code>// Each line is a rule

// a rule looks something like:

// &lt;name&gt; : &lt;list of things the rule can match&gt;

// where the list of things the rule can match is:
 
// &lt;name&gt; | &lt;name&gt; &lt;name&gt; | &lt;name&gt; &lt;name&gt; &lt;name&gt;
 
// where &lt;name&gt; is either the name of an operator or a keyword
 
// The grammar below is for addition, subtraction and multiplication
 
// (no division, no precedence, no negative numbers)
 
expression:
 
    term ("+" term | "-" term)*;
 
term:
    factor ("*" factor)*;
 
factor:
 
    INT;
 
// keywords
 
KEYWORD: "for" | "while" | "do" | "if" | "int" | "short" | "long";
 
// operators
 
OPERATOR: "*" | "+" | "-";
 
// numbers
 
INT: ('0'..'9')+;
 
WS: (' ' | '\t' | '\r' | '\n')+ {$channel = HIDDEN;};

</code>

Therefore,
Every rule is a simple sequence of <code>&lt;name&gt;</code> or <code>&lt;name&gt; &lt;name&gt;</code> or <code>&lt;name&gt; &lt;name&gt; &lt;name&gt;</code>, where <code>&lt;name&gt;</code> is a keyword or operator, therefore it conforms to the standard of an LL grammar.

It is not ambiguous because every term (a sequence of <code>&lt;factor&gt;</code> with <code>&lt;operator&gt;</code> in between) can match at most one sequence of <code>&lt;factor&gt; &lt;operator&gt; &lt;factor&gt;</code>. For example, the string <code>"1 + 2 * 3"</code> can match <code>&lt;expression&gt;</code> or <code>&lt;term&gt;</code> but it cannot match <code>&lt;term&gt; &lt;expression&gt;</code> because the <code>+</code> operator has a lower precedence than the <code>*</code> operator.
 
There are 3 rules: <code>&lt;expression&gt;</code>, <code>&lt;term&gt;</code> and <code>&lt;factor&gt;</code>.
The <code>&lt;expression&gt;</code> rule matches a sequence of <code>&lt;term&gt;</code> with <code>&lt;operator&gt;</code> in between.
The <code>&lt;term&gt;</code> rule matches a sequence of <code>&lt;factor&gt;</code> with <code>&lt;operator&gt;</code> in between.
The <code>&lt;factor&gt;</code> rule matches an integer.
The <code>KEYWORD</code> rule matches one of the keywords.
The <code>OPERATOR</code> rule matches one of the operators.
The <code>INT</code> rule matches an integer.
The <code>WS</code> rule matches whitespace.
 
The grammar is not ambiguous because it enforces the order of operations (the <code>&lt;expression&gt;</code> rule matches terms with <code>+</code> or <code>-</code> between them, and the <code>&lt;term&gt;</code> rule matches factors with <code>*</code> between them).
 
The grammar is LL(1) because it can be parsed with a single lookahead token. For example, to parse the <code>&lt;expression&gt;</code> rule, the parser would look at the next token, and if it is <code>+</code> or <code>-</code>, it would parse a <code>&lt;term&gt;</code>. If it is not <code>+</code> or <code>-</code>, it would parse a <code>&lt;factor&gt;</code>.
 
### e & f & g
/*Lex code to count total number of tokens */

%{

int n = 0 ;

%}

// rule section

%%

//count number of keywords

"while"|"if"|"else" {n++;printf("\t keywords : %s", yytext);}

// count number of keywords

"int"|"float" {n++;printf("\t keywords : %s", yytext);}

// count number of identifiers

[a-zA-Z_][a-zA-Z0-9_]* {n++;printf("\t identifier : %s", yytext);}

// count number of operators

"<="|"=="|"="|"++"|"-"|"*"|"+" {n++;printf("\t operator : %s", yytext);}

// count number of separators

[(){}|, ;] {n++;printf("\t separator : %s", yytext);}

// count number of floats

[0-9]*"."[0-9]+ {n++;printf("\t float : %s", yytext);}

// count number of integers

[0-9]+ {n++;printf("\t integer : %s", yytext);}

. ;

%%
 
int main()

{
 
yylex();
 
printf("\n total no. of token = %d\n", n);
 
}

![2](https://user-images.githubusercontent.com/99223665/202880191-1cb795bd-a5aa-49b2-9b58-a09d844fee12.png)

