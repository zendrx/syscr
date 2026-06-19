
# Hello World

Now that you have Crystal installed, you're ready to write your first program. This lesson will guide you through creating, running, and understanding the classic "Hello World" program in Crystal.

---

## What You'll Learn

- The basic structure of a Crystal program
- How to run Crystal code in development mode (interpreted) and production mode (compiled)
- The difference between `puts` and `print`
- How to compile your code into a standalone binary
- How to fix common beginner mistakes

---

## Your First Crystal Program

Open your terminal and create a directory for your Crystal projects:

```bash
mkdir ~/crystal_practice
cd ~/crystal_practice
```

Now create a file named hello.cr in this directory. You can use any text editor you like – VS Code, Vim, Nano, etc. For example, using Nano:

```bash
nano hello.cr
```

Type the following code:

```crystal
puts "Hello, World!"
```

Save the file (in Nano: Ctrl+O, Enter, then Ctrl+X to exit).

That's it. No main function, no extra boilerplate – Crystal runs top‑to‑bottom.

---

Running Your Program

Crystal provides two ways to execute your code.

1. Interpreted Mode (Development)

This mode compiles your code in memory and runs it immediately. Perfect for testing and quick iterations.

```bash
crystal hello.cr
```

You should see:

```
Hello, World!
```

2. Compiled Mode (Production)

Crystal can compile your program into a standalone binary. This binary is native machine code and runs without needing Crystal installed.

```bash
crystal build hello.cr --release
```

The --release flag enables optimizations (faster code, smaller binary). After compilation, you'll have an executable named hello (or hello.exe on Windows WSL).

Run it:

```bash
./hello
```

Output:

```
Hello, World!
```

You can check the binary size:

```bash
ls -lh hello
```

You'll see a ~1‑2 MB file – that's your entire program compiled to machine code.

---

Understanding the Code

The program consists of a single line:

```crystal
puts "Hello, World!"
```

puts is a built‑in method that prints its argument to the console, followed by a newline. It's short for "put string".

---

puts vs print

Crystal also has a print method, which does not add a newline:

```crystal
puts "Hello"
print "World"
puts "!"
```

Output:

```
Hello
World!
```

Notice "World!" stays on the same line because print doesn't add a newline, but the final puts adds it after printing.

---

Exercises

Exercise 1: Print Multiple Lines

Write a program that prints the following three lines:

```
Hello, Crystal!
I'm learning a new language.
It's fast and fun.
```

Save it as greeting.cr and run it.

<details>
<summary>Solution</summary>```crystal
puts "Hello, Crystal!"
puts "I'm learning a new language."
puts "It's fast and fun."
```

</details>Exercise 2: Combine puts and print

Write a program that prints:

```
Name: Alice
Age: 30
```

Use print for the labels and puts for the values, so everything appears on two lines (one for Name, one for Age).

<details>
<summary>Solution</summary>```crystal
print "Name: "
puts "Alice"
print "Age: "
puts "30"
```

</details>Exercise 3: Build a Binary

Compile greeting.cr to a binary and run it from the command line.

```bash
crystal build greeting.cr --release
./greeting
```

You should see the same output.

---

Common Errors

File not found

```bash
crystal hello.cr
Error: file not found 'hello.cr'
```

Make sure you are in the correct directory and the filename is spelled correctly.

Syntax errors

For example, missing a quote:

```crystal
puts "Hello, World!
```

Crystal will tell you the exact line and character position:

```
Syntax error in hello.cr:1: unterminated string literal
puts "Hello, World!
     ^
```

Always read the error message – it points you directly to the problem.

Missing closing parentheses (not necessary for puts but for other methods)

Crystal is flexible; you can omit parentheses for method calls. But if you use them, ensure they match.

---

What You Learned

- Crystal files use the .cr extension.
- puts prints text with a newline; print prints without.
- You can run Crystal code with crystal <file>.cr for development.
- You can compile to a binary with crystal build <file>.cr --release.
- The --release flag produces optimized machine code.
- Error messages are descriptive and helpful.

---

Next Steps

Now that you can print text, you're ready to learn about variables and data types. You'll store data and manipulate it.

Proceed to the next lesson: Variables and Types.
