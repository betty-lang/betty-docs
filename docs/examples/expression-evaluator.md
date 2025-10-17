# Expression Evaluator

This is a mathematical expression evaluator implemented in Betty, showcasing the language’s self-hosting (bootstrapping) potential.

```python
### GLOBALS ###
# Tokenizer
global text;
global pos;
global currentChar;
# Parser
global tokens;
global currentTokenIndex;
### END GLOBALS ###

### LEXER ###

func advance()
{
    pos++;
    if (pos >= len(text))
        currentChar = '\0';
    else
        currentChar = text[pos];
}

func skipWhitespace()
{
    while (currentChar != '\0' && isspace(currentChar))
        advance();
}

func initTokenizer(s)
{
    text = s;
    pos = 0;
    currentChar = text[pos];
}

func tokenize()
{
    # Initialize empty token list
    tokList = [];
    while (currentChar != '\0')
    {
        if (isspace(currentChar))
        {
            skipWhitespace();
            continue;
        }
        if (isdigit(currentChar))
        {
            number = "";
            while (isdigit(currentChar))
            {
                number += tostr(currentChar);
                advance();
            }
            tokList += [["Number", tonum(number)]];
            continue;
        }
        if (currentChar == '+'
            || currentChar == '-'
            || currentChar == '*'
            || currentChar == '/') 
            {
                tokList += [["BinOp", currentChar]];
                advance();
                continue;
            }
        if (currentChar == '(' || currentChar == ')')
        {
            tokList += [["Paren", currentChar]];
            advance();
            continue;
        }
        print("Error: Unrecognized character: " + currentChar + "\n");
        break;
    }
    return tokList;
}

### END LEXER ###

### PARSER ###

# Initializes the parser with the tokens produced by the tokenizer
func initParser(tokList)
{
    tokens = tokList;
    currentTokenIndex = 0;
}

# Returns the current token without advancing
func peekToken()
{
    if (currentTokenIndex < len(tokens))
        return tokens[currentTokenIndex];
    return ["EOF", 0]; # End of tokens
}

# Returns the next token and advances the cursor
func nextToken()
{
    token = peekToken();
    if (token[0] != "EOF")
        currentTokenIndex++;
    return token;
}

# Parse a factor: a number or an expression in parentheses
func parseFactor()
{
    token = nextToken();
    if (token[0] == "Number") 
    {
        return token[1]; # Return the numerical value
    } 
    elif (token[0] == "Paren" && token[1] == '(')
    {
        result = parseExpr(); # Parse the expression inside the parentheses
        closingParen = nextToken();
        if (closingParen[0] != "Paren" || closingParen[1] != ')')
        {
            println("Error: Expected ')'");
            return 0;
        }
        return result;
    }
    println("Error: Unexpected token in factor");
    return 0;
}

# Parse a term: a factor followed by '*' or '/' operators
func parseTerm()
{
    result = parseFactor();
    while (true)
    {
        token = peekToken();
        if (token[0] == "BinOp" && (token[1] == '*' || token[1] == '/'))
        {
            nextToken(); # Consume the operator
            if (token[1] == '*')
            {
                result *= parseFactor();
            }
            elif (token[1] == '/')
            {
                result /= parseFactor();
            }
        }
        else 
        {
            break;
        }
    }
    return result;
}

# Parse an expression: a term followed by '+' or '-' operators
func parseExpr() 
{
    result = parseTerm();
    while (true) 
    {
        token = peekToken();
        if (token[0] == "BinOp" && (token[1] == '+' || token[1] == '-'))
        {
            nextToken(); # Consume the operator
            if (token[1] == '+') 
            {
                result += parseTerm();
            } 
            elif (token[1] == '-') 
            {
                result -= parseTerm();
            }
        } 
        else 
        {
            break;
        }
    }
    return result;
}

# Main evaluation function that wraps the tokenizer and parser initialization and starts the parsing process
func evaluate(expr) 
{
    # Initialize the tokenizer
    initTokenizer(expr);
    # Tokenize the expression first
    tokenList = tokenize();
    # Initialize the parser with the token list
    initParser(tokenList);
    # Start parsing from the expression level
    result = parseExpr();
    println("Result: ", result);
}

### END PARSER ###

# Entry point
func main() 
{
    while (true) 
    {
        expr = input("> ");
        evaluate(expr);
    }
}
```