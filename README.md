# Jlox - interpreter
A Lox interpreter implemented in Java, following the book "Crafting Interpreters" by Robert Nystrom.

## Quick Start 🚀

Want to try the interpreter right away? Here's how:

### 1. Install JDK (if not already installed)
```bash
# Ubuntu/Debian
sudo apt update && sudo apt install openjdk-11-jdk

# macOS
brew install openjdk@11

# Verify installation
java -version
javac -version
```

### 2. Clone and run the scanner
```bash
git clone <your-repo-url>
cd Jlox-interpreter
mvn clean compile
mvn exec:java -Dexec.mainClass="com.jlox.Lox"
```

### 3. Try the REPL
```bash
> print "Hello, World!";
> var x = 42;
> print x + 8;
```

**Note:** Currently only the scanner (tokenizer) is implemented. The interpreter will show you the tokens it recognizes!

## What Works Now ✅

- **Scanner/Lexer**: Tokenizes Lox source code
- **REPL Mode**: Interactive command-line interface
- **File Mode**: Read and tokenize `.lox` files
- **Error Reporting**: Shows line numbers for errors

## Project Development TODOs 📋

Here's the step-by-step roadmap to complete the interpreter:

### Phase 1: Core Parser (Next Priority)
- [ ] **Parser.java**: Implement recursive descent parser
- [ ] **Expr.java**: Define expression AST nodes (binary, unary, literal, etc.)
- [ ] **Stmt.java**: Define statement AST nodes (print, expression, var, etc.)
- [ ] **Test parser**: Create unit tests for parsing

### Phase 2: Basic Interpreter
- [ ] **Interpreter.java**: Implement tree-walking interpreter
- [ ] **Environment.java**: Variable storage and scoping
- [ ] **Runtime errors**: Better error handling
- [ ] **Test interpreter**: Basic arithmetic and variables

### Phase 3: Control Flow
- [ ] **If statements**: Conditional execution
- [ ] **While loops**: Iteration
- [ ] **For loops**: Syntactic sugar for while
- [ ] **Test control flow**: Comprehensive test suite

### Phase 4: Functions
- [ ] **Function declarations**: `fun` keyword
- [ ] **Function calls**: Parameter passing and return values
- [ ] **Closures**: Lexical scoping
- [ ] **Native functions**: Built-in functions like `clock()`

### Phase 5: Classes (Advanced)
- [ ] **Class declarations**: `class` keyword
- [ ] **Instance methods**: Method calls on objects
- [ ] **Inheritance**: `super` keyword
- [ ] **Constructors**: `init` method

## How to Run the Lox Interpreter

### Using Maven (Recommended)
```bash
# Compile the project
mvn clean compile

# Run REPL mode
mvn exec:java -Dexec.mainClass="com.jlox.Lox"

# Run a Lox file
mvn exec:java -Dexec.mainClass="com.jlox.Lox" -Dexec.args="script.lox"

# Create executable JAR
mvn package
java -jar target/jlox-interpreter-1.0-SNAPSHOT.jar
```

### Alternative: Direct Java Compilation
```bash
# Compile all Java files
javac -d target/classes src/main/java/com/jlox/*.java

# Run the interpreter
java -cp target/classes com.jlox.Lox

# Run with a file
java -cp target/classes com.jlox.Lox script.lox
```

## Testing the Current Scanner

Create a test file `test.lox`:
```lox
// This is a comment
var name = "World";
var number = 42;
print "Hello, " + name + "!";
print number * 2;

if (number > 40) {
    print "Big number!";
}
```

Run it:
```bash
mvn exec:java -Dexec.mainClass="com.jlox.Lox" -Dexec.args="test.lox"
```

You'll see the tokens the scanner produces!

## Prerequisites

### Installing JDK

This project requires Java Development Kit (JDK) 11 or higher:

#### Ubuntu/Debian
```bash
sudo apt update
sudo apt install openjdk-11-jdk
java -version && javac -version
```

#### macOS
```bash
brew install openjdk@11
export PATH="/usr/local/opt/openjdk@11/bin:$PATH"
java -version && javac -version
```

#### Windows
1. Download JDK 11 from [Oracle](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
2. Add `JAVA_HOME` and update PATH
3. Verify: `java -version` and `javac -version`

#### Using SDKMAN! (Cross-platform)
```bash
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
sdk install java 11.0.21-tem
```

### Installing Maven

```bash
# Ubuntu/Debian
sudo apt install maven

# macOS
brew install maven

# Verify
mvn -version
```

## Project Structure

```
src/
├── main/java/com/jlox/
│   ├── Lox.java          # ✅ Main entry point
│   ├── Scanner.java      # ✅ Lexical analyzer
│   ├── Token.java        # ✅ Token representation
│   ├── TokenType.java    # ✅ Token types enum
│   ├── Parser.java       # ⏳ Syntax analyzer (TODO)
│   ├── Expr.java         # ⏳ Expression AST nodes (TODO)
│   ├── Stmt.java         # ⏳ Statement AST nodes (TODO)
│   └── Interpreter.java  # ⏳ Tree-walking interpreter (TODO)
└── test/java/com/jlox/   # Unit tests
```

## Example Lox Code (Future Features)

```lox
// Variables
var name = "Lox";
var number = 42;

// Arithmetic
print 1 + 2 * 3;

// Control flow
if (number > 40) {
    print "Big number!";
} else {
    print "Small number.";
}

// Functions
fun greet(name) {
    print "Hello, " + name + "!";
}

greet("World");
```

## Common Issues

1. **"No compiler is provided in this environment"**
   - Install JDK (not just JRE) following instructions above

2. **"command not found: mvn"**
   - Install Maven following instructions above

3. **Package declaration errors**
   - Ensure all Java files use `package com.jlox;`

## Resources

- [Crafting Interpreters Book](https://craftinginterpreters.com/)
- [Lox Language Reference](https://craftinginterpreters.com/the-lox-language.html)
- [Maven Documentation](https://maven.apache.org/guides/)
- [Java 11 Documentation](https://docs.oracle.com/en/java/javase/11/)

## Contributing

1. Pick a TODO from the development roadmap above
2. Create a feature branch
3. Implement the feature with tests
4. Submit a pull request

Happy coding! 🎉