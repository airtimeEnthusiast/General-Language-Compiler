
# Basic Compiler

A small compiler that reads and executes a small program. The compiler then interprets the generated list of instructions, traversing the data structure and executing each node, which involves modifying memory locations corresponding to operands and determining the next instruction to execute. The compiler's output should match the expected output of the input program.

### Compiler Grammer
| Rule           | Structure 								|
|----------------|----------------------------------------------------------------------|
| program      → |  var_section body inputs                                             |
| var_section  → |  id list SEMICOLON                                                   |
| id list      → | ID COMMA id_list | ID                                                |
| body         → | LBRACE stmt_list RBRACE                                              |
| stmt_list    → | stmt_list | stmt                                                     |
| stmt         → | assign_stmt | while_stmt | if_stmt | switch_stmt | for_stmt          |
| stmt         → | output_stmt | input_stmt                                             |
| assign_stmt  → | ID EQUAL primary SEMICOLON                                           |
| assign_stmt  → | ID EQUAL expr SEMICOLON                                              |
| expr         → | primary op primary                                                   |
| primary      → | ID | NUM                                                             |
| op           → | PLUS | MINUS | MULT | DIV                                            |
| output_stmt  → | output ID SEMICOLON                                                  |
| input_stmt   → | input ID SEMICOLON                                                   |
| while_stmt   → | WHILE condition body                                                 |
| if_stmt      → | IF condition body                                                    |
| condition    → | primary relop primary                                                |
| relop        → | GREATER | LESS | NOTEQUAL                                            |
| switch_stmt  → | SWITCH ID LBRACE case_list RBRACE                                    |
| switch_stmt  → | SWITCH ID LBRACE case_list default_case RBRACE                       |
| for_stmt     → | FOR LPRAEN assign_stmt condition SEMICOLON assign_stmt RPAREN body   |
| case_list    → | case case_list | case                                                |
| default_case → | DEFAULT COLON body                                                   |
| inputs       → | num_list                                                             |
| num_list     → | NUM                                                                  |
| num_list     → |NUM num_list                                                          |

### How to Use

 Write your input program in a text file, e.g., 'input_program.txt' or use one of the provided test cases
```bash
  ./a.out < input_program
```

### Example input

```css
a, b;
{
  a , b, c, i;
{
a = 1;
b = 1;
output a;
output b;

i = 3;
WHILE i < 10 {
        c = a + b;
	output c;
        a = b;
        b = c;
	i = i+1;
}

}
3 2 1 4 2
```
[Source Code](https://github.com/airtimeEnthusiast/Simple_Compiler/tree/main)
