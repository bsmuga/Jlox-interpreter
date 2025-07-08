# Jlox - interpreter
A Lox interpreter implemented in Java, following the book "Crafting Interpreters" by Robert Nystrom.

## Prerequisites

### Installing JDK

This project requires Java Development Kit (JDK) 11 or higher. Here's how to install it:

#### Ubuntu/Debian
```bash
# Update package index
sudo apt update

# Install OpenJDK 11
sudo apt install openjdk-11-jdk

# Verify installation
java -version
javac -version
```

#### macOS
```bash
# Using Homebrew
brew install openjdk@11

# Add to PATH (add this to your ~/.zshrc or ~/.bash_profile)
export PATH="/usr/local/opt/openjdk@11/bin:$PATH"

# Verify installation
java -version
javac -version
```

#### Windows
1. Download JDK 11 from [Oracle](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) or [OpenJDK](https://adoptopenjdk.net/)
2. Run the installer
3. Add `JAVA_HOME` to your environment variables:
   - Set `JAVA_HOME` to your JDK installation directory (e.g., `C:\Program Files\Java\jdk-11`)
   - Add `%JAVA_HOME%\bin` to your PATH
4. Verify installation in Command Prompt:
   ```cmd
   java -version
   javac -version
   ```

#### Alternative: Using SDKMAN! (Cross-platform)
```bash
# Install SDKMAN!
curl -s "https://get.sdkman.io" | bash

# Open new terminal or source the script
source "$HOME/.sdkman/bin/sdkman-init.sh"

# Install Java 11
sdk install java 11.0.21-tem

# Verify installation
java -version
```

### Installing Maven

#### Ubuntu/Debian
```bash
sudo apt install maven
```

#### macOS
```bash
brew install maven
```

#### Windows
1. Download Maven from [Apache Maven](https://maven.apache.org/download.cgi)
2. Extract to a directory (e.g., `C:\Program Files\Apache\maven`)
3. Add Maven to PATH environment variable
4. Verify: `mvn -version`

## Building and Running

### Compile the project
```bash
mvn clean compile
```

### Run the REPL (interactive mode)
```bash
mvn exec:java -Dexec.mainClass="com.jlox.Lox"
```

### Run a Lox script file
```bash
mvn exec:java -Dexec.mainClass="com.jlox.Lox" -Dexec.args="script.lox"
```

### Create executable JAR
```bash
mvn package
java -jar target/jlox-interpreter-1.0-SNAPSHOT.jar
```

### Run tests
```bash
mvn test
```

## Development Tips

### Project Structure
```
src/
├── main/java/com/jlox/
│   ├── Lox.java          # Main entry point
│   ├── Scanner.java      # Lexical analyzer
│   ├── Token.java        # Token representation
│   ├── TokenType.java    # Token types enum
│   ├── Parser.java       # Syntax analyzer (to be implemented)
│   ├── Expr.java         # Expression AST nodes (to be implemented)
│   ├── Stmt.java         # Statement AST nodes (to be implemented)
│   └── Interpreter.java  # Tree-walking interpreter (to be implemented)
└── test/java/com/jlox/   # Unit tests
```

### Current Implementation Status
- ✅ Scanner (Lexer) - Converts source code to tokens
- ✅ Token system - Token types and representation
- ⏳ Parser - Converts tokens to AST (not implemented)
- ⏳ Interpreter - Executes the AST (not implemented)

### Example Lox Code
```lox
// Variable declaration
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

// Loops
for (var i = 0; i < 5; i = i + 1) {
    print i;
}

// Functions
fun greet(name) {
    print "Hello, " + name + "!";
}

greet("World");
```

### Common Issues

1. **"No compiler is provided in this environment"**
   - You have JRE instead of JDK. Install JDK following the instructions above.

2. **Package declaration errors**
   - Ensure all Java files use `package com.jlox;`

3. **Maven not found**
   - Install Maven following the instructions above.

### Next Steps

1. Implement the Parser to build Abstract Syntax Trees (AST)
2. Define AST node classes in Expr.java and Stmt.java
3. Implement the tree-walking Interpreter
4. Add more language features (functions, classes, etc.)

## Resources

- [Crafting Interpreters Book](https://craftinginterpreters.com/)
- [Lox Language Reference](https://craftinginterpreters.com/the-lox-language.html)
- [Maven Documentation](https://maven.apache.org/guides/)
- [Java 11 Documentation](https://docs.oracle.com/en/java/javase/11/)