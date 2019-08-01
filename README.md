Loose feature list:
* Generate token definitions
* Parse tokens from text (tokenize)
  * Allow for skipping
* Parse grammar from tokens
  * Allow store token's actual value
  * Allow named tokens/grammar tokens
  * Allow repeated grammar tokens
* Build program tree
* Evaluate program tree
  * Evaluate() function?
  * Allow includes



Compiler:
// State context-like process
- step: CompilerStep  // first/current step
+ step(): void  // execute and print a single CompilerStep
+ runAll(): void  // run all CompilerSteps, but print only the result
+ stepAll(): void  // execute and print each step

CompilerStep:
// A single step in the REPL sequence
- compiler: Compiler
+ run(): CompilerStep  // returns next step, or null if done
+ toString(): string



TokenDef
// Token definition
- name: string
- regex: string
- ignored: boolean
+ getName(): string
+ getMatches(): Token[]

Token
// Generic token
- name: string
+ getName: string
+ evaluate(): Value

LexicalToken : Token
// Actual lexical token
- name: string
- value: string
+ getName(): string
+ getValue(): string

GrammarToken : Token
// Runnable grammar element
- name: string
- values: map<name: string, value: string>
- children: Token[]



Value
// Represents a primitive value

IntValue : Value
- value: string
+ getValue(): string

StrValue : Value
- value: string
+ getValue(): string