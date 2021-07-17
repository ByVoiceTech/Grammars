# Grammars

This repository contains open source versions of commonly used grammars and their delegates.

## Syntax

Simple BNF style definitions, grammar names are surrounded by \<\>. Identifiers (words and grammar names within \<\>) must begin with a letter, can include numbers (after first letter), and may be upper or lower case:

    <Digit> = [one two three four five six seven eight nine zero oh];
    
    <Telephone> = +<Digit>;
    
    <Command> = [call dial phone] <Telephone>;

With a function (trailing semicolon optional after close brace):

    <GrammarName> = expression { myFunction($*); }

Comments begin with hash, extend only to end of line:

    # This is a comment.
    <Hello> = [hi hello welcome greetings]; # Another comment.

Expression operators use prefix placement:

| Operator | Characters | Description | Example |
| -------- | ---------- | ----------- | ------- |
| AND | ( ) | Spoken in sequence | (the new york times) |
| OR | \[ \] | Alternatives | \[cat dog mouse horse cow\] |
| OPT | ? | Optional word or grammar | the ?tall tree |
| LOOP | + | One or more of | toppings are \+\[pepperoni cheese sausage ham\] |
| KLEENE | * | Zero or more of | thank you \*very much |

The default operator for a grammar definition is AND:

    <Newspaper> = the new york times;

NULL productions are disallowed, meaning a grammar must map to at least one word.
To effect a NULL, use the OPT or KLEENE operators, but the grammar containing it
must still produce at least one word. This prevents "infinite loops" should null
productions be encountered in parsing.

    # NOT ALLOWED, CAN PRODUCE NULL FOR GRAMMAR
    <Digit> = *[one two three four];
    
    # OKAY, NULL IS INSIDE NON-NULL GRAMMAR
    <Order> = i want a *[small medium large] pizza;
    
Acronyms should use periods in their word identifiers:

    <Channel> = [E.S.P.N. A.B.C. C.B.S. C.N.N.];

Optional plurals can use underscore:

    <MoneyAmount> = [one two] dollar_s;

Top-level grammar should be defined last (at bottom of file), and uses period syntax without \<\>:

    .TimerApp = [<SetTimer> <QueryTimer> <CancelTimer>];
