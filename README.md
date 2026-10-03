# 🔥 Kindling

**Kindling** is the tooling around **Spark**, a small programming language built from scratch in Python: a hand-written lexer, a recursive-descent parser, and a tree-walking interpreter. No parser-generator libraries, no external dependencies.

**[▶ Try Kindling in the browser](https://berenguzen.github.io/kindling/playground/)**

A JavaScript port of the interpreter runs entirely client-side, so you can write and run Spark programs without installing anything. The source is in [`playground/`](./playground).

---

## What's in this repo

| Part | What it is |
|------|------------|
| **Spark** | The language itself: `lexer.py`, `parser.py`, `nodes.py`, `interpreter.py`, `main.py`. Run `.spark` files from the command line. |
| **Kindling** | The browser playground for Spark, in `playground/`: an editor, a run button, and an output panel in one self-contained HTML page. |

## Language features

- Variables with `let`
- Arithmetic and comparison operators: `+ - * / == != > < >= <=`
- Logical `and` / `or` with short-circuit evaluation
- `if` / `else`
- `while` loops
- Functions with closures (`func`, `return`)
- Arrays and indexing (`[1, 2, 3]`, `arr[0]`)
- Strings and booleans
- Built-ins: `print()`, `len()`, `int()`
- Comments with `#`

## Example

```spark
func fib(n) {
    if n <= 1 {
        return n
    }
    return fib(n - 1) + fib(n - 2)
}

let i = 0
while i < 10 {
    print(fib(i))
    i = i + 1
}
```

More programs in [`examples/`](./examples).

## Quick start

Requires Python 3.

```bash
git clone https://github.com/berenguzen/kindling.git
cd kindling

python3 main.py examples/fibonacci.spark
python3 main.py examples/fizzbuzz.spark
```

Or just open `playground/index.html` in any browser. It works offline.

## How the interpreter works

```
source code → lexer → tokens → parser → AST → interpreter → output
```

- **`lexer.py`**: turns source text into a flat list of tokens.
- **`parser.py`**: a recursive-descent parser that turns tokens into an AST (the grammar is in its docstring).
- **`nodes.py`**: the AST node definitions.
- **`interpreter.py`**: walks the AST directly and executes it (no bytecode or VM step).
- **`main.py`**: CLI entry point; reads a `.spark` file and runs it.

## Project structure

```
kindling/
├── lexer.py
├── parser.py
├── nodes.py
├── interpreter.py
├── main.py
├── examples/
│   ├── fibonacci.spark
│   └── fizzbuzz.spark
└── playground/
    └── index.html      # Kindling: the browser playground (JS port of the interpreter)
```

## License

MIT
