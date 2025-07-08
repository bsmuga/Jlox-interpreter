# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Lox programming language interpreter implemented in Java, following the structure from Robert Nystrom's "Crafting Interpreters" book. The project is in early development stages with the basic token system in place but scanner, parser, and interpreter components yet to be fully implemented.

## Critical Issues to Address

1. **Package Name Mismatch**: Files are located in `com/jlox/` directory but declare package `com.craftinginterpreters.lox`. This must be fixed before the project can compile.
2. **Empty pom.xml**: The Maven configuration file needs to be populated.
3. **Syntax Error**: Line 47 in `Lox.java` has `Token.token` which should be just `token`.
4. **Filename Typo**: `Intepreter.java` should be renamed to `Interpreter.java`.

## Build and Run Commands

### Prerequisites
- Java 11 or higher
- Maven 3.6 or higher

### Build Commands
```bash
# Clean and compile
mvn clean compile

# Run tests
mvn test

# Package into JAR
mvn package

# Full build cycle
mvn clean compile test package
```

### Run Commands
```bash
# Run REPL mode
mvn exec:java -Dexec.mainClass="com.jlox.Lox"

# Run a Lox script file
mvn exec:java -Dexec.mainClass="com.jlox.Lox" -Dexec.args="script.lox"

# Using JAR (after packaging)
java -jar target/jlox-interpreter-1.0-SNAPSHOT.jar
java -jar target/jlox-interpreter-1.0-SNAPSHOT.jar script.lox
```

### Development Commands
```bash
# Run a specific test class
mvn test -Dtest=LoxTest

# Run a specific test method
mvn test -Dtest=LoxTest#testScanner

# Skip tests during build
mvn package -DskipTests
```

## Architecture Overview

### Core Components

1. **Lox.java**: Main entry point
   - Handles REPL and file execution modes
   - Manages error reporting
   - Orchestrates the interpreter pipeline

2. **Scanner.java**: Lexical analyzer (to be implemented)
   - Converts source code into tokens
   - Handles single and multi-character lexemes
   - Tracks line numbers for error reporting

3. **Token System**:
   - `Token.java`: Represents individual tokens with type, lexeme, literal value, and line number
   - `TokenType.java`: Enum of all token types (operators, keywords, literals, etc.)

4. **Parser.java**: Syntax analyzer (empty stub)
   - Will convert tokens into an Abstract Syntax Tree (AST)

5. **AST Nodes**:
   - `Expr.java`: Expression nodes (empty stub)
   - `Stmt.java`: Statement nodes (empty stub)

6. **Interpreter.java**: Tree-walking interpreter (empty stub, currently misspelled as "Intepreter.java")
   - Will execute the AST

7. **Advanced Features** (empty stubs):
   - `Resolver.java`: Variable resolution pass
   - `LoxClass.java`, `LoxInstance.java`, `LoxFunction.java`: Object-oriented features

### Interpreter Pipeline
```
Source Code → Scanner → Tokens → Parser → AST → Resolver → Interpreter → Result
```

### Error Handling
- Errors include line numbers for debugging
- Static `error()` method in Lox class for centralized error reporting
- `hadError` flag prevents execution of erroneous code

## Current Implementation Status

- ✅ Basic project structure
- ✅ Token and TokenType classes
- ✅ Main entry point with REPL and file modes
- ⚠️ Scanner started but not implemented
- ❌ Parser not implemented
- ❌ AST nodes not implemented
- ❌ Interpreter not implemented
- ❌ Advanced features not implemented

## Development Guidelines

1. **Follow Crafting Interpreters patterns**: The project follows the book's architecture closely
2. **Maintain separation of concerns**: Each phase of interpretation has its own class
3. **Error handling**: Always include line numbers in error messages
4. **Testing**: Add unit tests for each component as it's implemented
5. **Package consistency**: Ensure all files use consistent package declarations

## Next Steps for Implementation

1. Fix the package declaration issue (decide between `com.jlox` or `com.craftinginterpreters.lox`)
2. Populate pom.xml with proper Maven configuration
3. Fix the syntax error in Lox.java
4. Implement the Scanner class to tokenize input
5. Add unit tests for the Scanner
6. Implement the Parser to build ASTs
7. Define the AST node classes in Expr.java and Stmt.java
8. Implement the tree-walking Interpreter