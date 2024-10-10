
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

### Example Input
Programs are in text file e.g., 'input_program.txt'.
| Input Program Lines              | Statements								|
|-------------------|---------------------------------------------------------------------------|
| 1 	    | Contains declaration statements for the variables *a*, *b*, *c*, and *d*.
| 3-6         | Assigns the variables to integers.
| 7-10        | Contains a SWITCH statment where CASE 2 is executed and the value of *b* is "2".
| 11           | Has an ADD statement where *d* now has the value 5.
| 12-15       | Defines a WHILE loop where d is decremented and printed 5 times.
| 17-19       | Contains an IF statement that evaluates to true so the value of a is printed.
| 32           | Lists some indices: 10, 2, 3, and 1 for the variables a, b, c, and d to be stored in an input vector. This keeps track of which values to read at runtime.
```c++
1 a, b, c, d;
2 {
3 	a = 1 ;
4	b = 2 ;
5	c = 3 ;
6	d = 4 ;
7		SWITCH b {
8			CASE 1: { output a;}
9			CASE 2: { output b;}
10		}
11		d = d + 1;
12	WHILE d > 0 {
13		output d;
14		d = d-1;
15	}
16
17	IF c > b { 
18		output a;
19	}
20 }
21 10 2 3 1
```
### Execution
- The input file above is fed into the program via standard input.
```bash
  ./a.out < input_program.txt
```

#### Output
- Will print every output statement in order.
<p align="left">
  <img src="assets/compiler_output.png?raw=true" alt="cat" />
</p>

[Source Code](https://github.com/airtimeEnthusiast/Simple_Compiler/tree/main)
