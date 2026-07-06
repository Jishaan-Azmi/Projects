<div align="center">

<h1>CodeScript</h1>

<p>A beginner-friendly programming language that transpiles to JavaScript.</p>

<p>
  <img src="https://img.shields.io/badge/version-1.0.0-blue?style=flat-square" alt="version" />
  <img src="https://img.shields.io/badge/language-TypeScript-3178c6?style=flat-square" alt="typescript" />
  <img src="https://img.shields.io/badge/runtime-Node.js-339933?style=flat-square" alt="nodejs" />
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="license" />
  <img src="https://img.shields.io/badge/status-active-brightgreen?style=flat-square" alt="status" />
</p>

</div>

---

## What is CodeScript?

CodeScript is a lightweight, readable programming language that compiles to JavaScript. It replaces confusing syntax with plain English keywords so beginners can focus on learning programming logic instead of fighting the language.

Every `.code` file you write is transpiled into clean, readable JavaScript and executed by Node.js.

```code
make name = "Zishan"

do greet(person){
    say("Hello " + person)
    give person
}

greet(name)
```

```javascript
// Generated JavaScript
let name = "Zishan";

function greet(person){
    console.log("Hello " + person);
    return person;
}

greet(name);
```

---

## Why CodeScript?

| Problem | CodeScript Solution |
|---|---|
| `console.log` is confusing | Use `say` instead |
| `let`, `const`, `var` are unclear | Use `make` and `fixed` |
| `function` keyword is verbose | Use `do` |
| `this` is confusing | Use `me` |
| `try/catch/finally` is intimidating | Use `attempt/oops/done` |
| `new` keyword feels magical | Use `create` |
| `null` and `undefined` are unclear | Use `empty` and `unknown` |

---

## Installation

**Requirements:** Node.js 18 or higher

```bash
npm install -g @codescript/cli
```

Verify installation:

```bash
codescript --version
```

---

## Quick Start

**1. Create your first file**

```bash
# Create hello.code
```

```code
say("Hello, World!")
```

**2. Run it**

```bash
codescript hello.code
```

**Output:**

```
Hello, World!
```

---

## CLI Commands

| Command | Description |
|---|---|
| `codescript <file.code>` | Compile and run a file |
| `codescript build <file.code>` | Compile only — outputs a `.js` file |
| `codescript watch <file.code>` | Watch for changes and recompile automatically |
| `codescript init` | Scaffold a new CodeScript project |
| `codescript --version` | Show the installed version |
| `codescript --help` | Show usage information |

---

## Compiler Pipeline

Every `.code` file passes through these stages before execution:

```
Source (.code)
      │
      ▼
    Lexer          →  Converts characters into tokens
      │
      ▼
   Parser          →  Converts tokens into an AST
      │
      ▼
     AST            →  Abstract Syntax Tree (program structure)
      │
      ▼
 Semantic Analyzer  →  Validates scope, types, and rules
      │
      ▼
  Optimizer         →  Constant folding, dead code removal
      │
      ▼
JS Generator        →  Emits clean JavaScript
      │
      ▼
  Node.js           →  Executes the output
```

---

## Keyword Reference

### Variables & Constants

| Keyword | JavaScript | Description |
|---|---|---|
| `make` | `let` | Declares a mutable variable |
| `fixed` | `const` | Declares an immutable constant — must be initialized |
| `keep` | `var` | Legacy variable — function scoped, avoid in new code |

```code
make age = 20
fixed PI = 3.14159
keep counter = 0
```

---

### Functions

| Keyword | JavaScript | Description |
|---|---|---|
| `do` | `function` | Declares a reusable function |
| `give` | `return` | Returns a value from a function |
| `later` | `async` | Marks a function as asynchronous |
| `wait` | `await` | Waits for an async operation to complete |

```code
do add(a, b){
    give a + b
}

later do fetchData(url){
    make result = wait fetch(url)
    give result
}
```

---

### Output & Input

| Keyword | JavaScript | Description |
|---|---|---|
| `say` | `console.log` | Prints a value to the console |

```code
say("Hello World")
say(42)
say(user.name)
```

---

### Conditions

| Keyword | JavaScript | Description |
|---|---|---|
| `check` | `if` | Executes a block when the condition is true |
| `otherwise` | `else` | Executes when the `check` condition is false |
| `pick` | `switch` | Selects one path from multiple options |
| `when` | `case` | Defines a single case inside a `pick` block |
| `anyway` | `default` | The fallback case inside a `pick` block |

```code
check(age >= 18){
    say("Adult")
}otherwise{
    say("Minor")
}

pick(day){
    when "Monday"{
        say("Start of the week")
    }
    when "Friday"{
        say("Almost weekend")
    }
    anyway{
        say("Regular day")
    }
}
```

---

### Loops

| Keyword | JavaScript | Description |
|---|---|---|
| `repeat` | `for` | Repeats a block a set number of times |
| `until` | `while` | Repeats while a condition is true |
| `stop` | `break` | Exits the nearest loop immediately |
| `skip` | `continue` | Skips the current iteration and continues |

```code
repeat(make i = 0; i < 5; i++){
    say(i)
}

make count = 0
until(count < 10){
    say(count)
    count++
}

repeat(make i = 0; i < 10; i++){
    check(i == 5){ stop }
    check(i == 3){ skip }
    say(i)
}
```

---

### Classes & OOP

| Keyword | JavaScript | Description |
|---|---|---|
| `type` | `class` | Declares a class |
| `from` | `extends` | Inherits from a parent class |
| `create` | `new` | Creates a new instance of a class |
| `me` | `this` | Refers to the current object instance |
| `parent` | `super` | Calls the parent class constructor or method |
| `shared` | `static` | Declares a static method or property |
| `mine` | `private` | Marks a member as private |
| `everyone` | `public` | Marks a member as public |
| `family` | `protected` | Marks a member as protected |

```code
type Animal{
    do constructor(name){
        me.name = name
    }
    do speak(){
        say("I am " + me.name)
    }
}

type Dog from Animal{
    do constructor(name){
        parent(name)
    }
}

make dog = create Dog("Rex")
dog.speak()
```

---

### Error Handling

| Keyword | JavaScript | Description |
|---|---|---|
| `attempt` | `try` | Wraps code that might throw an error |
| `oops` | `catch` | Handles the error if one is thrown |
| `panic` | `throw` | Throws an error and stops execution |
| `done` | `finally` | Always runs after attempt/oops, error or not |

```code
attempt{
    panic "Something went wrong"
}oops(err){
    say(err)
}done{
    say("Finished")
}
```

---

### Modules

| Keyword | JavaScript | Description |
|---|---|---|
| `grab` | `import` | Imports code from another `.code` file |
| `share` | `export` | Exports variables, functions, or classes |

```code
// math.code
do add(a, b){
    give a + b
}
share add

// main.code
grab { add } from "./math.code"
say(add(5, 3))
```

---

### Boolean & Null Values

| Keyword | JavaScript | Description |
|---|---|---|
| `yes` | `true` | Boolean true value |
| `no` | `false` | Boolean false value |
| `empty` | `null` | Represents an intentionally absent value |
| `unknown` | `undefined` | Represents an uninitialized value |

```code
make loggedIn = yes
make guest = no
make user = empty
make value = unknown
```

---

### Utility Keywords

| Keyword | JavaScript | Description |
|---|---|---|
| `kind` | `typeof` | Returns the type of a value as a string |
| `is` | `instanceof` | Checks if an object is an instance of a class |
| `remove` | `delete` | Deletes a property from an object |

```code
say(kind age)           // "number"
say(dog is Animal)      // true
remove user.email
```

---

## Complete Example

```code
// Variables
make name = "Zishan"
fixed PI = 3.14

// Function
do greet(person){
    say("Hello " + person)
    give person
}

greet(name)

// Condition
check(PI > 3){
    say("PI is greater than 3")
}otherwise{
    say("PI is small")
}

// Loop
repeat(make i = 1; i < 4; i++){
    say(i)
}

// Array
make fruits = ["Apple", "Banana", "Orange"]
say(fruits[0])

// Object
make user = { name: "Alex", age: 20 }
say(user.name)

// Class
type Animal{
    do constructor(name){
        me.name = name
    }
    do speak(){
        say("I am " + me.name)
    }
}

type Dog from Animal{
    do constructor(name){
        parent(name)
    }
}

make dog = create Dog("Rex")
dog.speak()

// Error Handling
attempt{
    panic "something went wrong"
}oops(err){
    say(err)
}done{
    say("finished")
}
```

**Output:**

```
Hello Zishan
PI is greater than 3
1
2
3
Apple
Alex
I am Rex
something went wrong
finished
```

---

## Project Structure

```
codescript/
├── packages/
│   ├── cli/          CLI — command line interface
│   ├── compiler/     Compiler orchestrator
│   ├── lexer/        Lexer — source to tokens
│   ├── tokenizer/    Token type definitions
│   ├── parser/       Parser — tokens to AST
│   ├── ast/          AST node definitions
│   ├── semantic/     Semantic analyzer
│   ├── optimizer/    AST optimizer
│   ├── generator/    JavaScript code generator
│   ├── resolver/     Module resolver
│   ├── stdlib/       Standard library
│   └── shared/       Shared utilities
├── examples/         Example .code programs
├── tests/            Automated tests
├── docs/             Language documentation
└── README.md
```

---

## Error Messages

CodeScript produces beginner-friendly compiler errors with file, line, column, and a suggested fix.

```
SyntaxError
File: hello.code
Line: 12
Column: 8
Message: Expected '}' but found ')'
Suggestion: Close the previous block before ending the function.
```

---

## Roadmap

| Milestone | Status |
|---|---|
| Documentation | ✅ Complete |
| Project Setup | ✅ Complete |
| CLI | ✅ Complete |
| Lexer | ✅ Complete |
| Parser + AST | ✅ Complete |
| Semantic Analyzer | ✅ Complete |
| Optimizer | ✅ Complete |
| JavaScript Generator | ✅ Complete |
| Standard Library | 🔄 In Progress |
| Module Resolver | 🔄 In Progress |
| Tests | ⏳ Planned |
| VS Code Extension | ⏳ Planned |
| Playground | ⏳ Planned |
| Website | ⏳ Planned |
| Version 1.0 Release | ⏳ Planned |

---

## License

MIT © Mohd Jishaan Azmi
