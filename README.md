# Grammars

This repository contains open source versions of commonly used grammars and their delegates.

## Syntax

| Operator | Characters | Description | Example |
| -------- | ---------- | ----------- | ------- |
| AND | ( ) | Spoken in sequence | (the new york times) |
| OR | \[ \] | Alternatives | \[cat dog mouse horse cow\] |
| OPT | ? | Optional word or grammar | the ?tall tree |
| LOOP | + | One or more of | toppings are \+\[pepperoni cheese sausage ham\] |
| KLEENE | * | Zero or more of | thanks \*very much |

NULL productions are disallowed, meaning a grammar must map to at least one word.
To effect a NULL, use the OPT or KLEENE operators, but the grammar containing it
must still produce at least one word. This prevents "infinite loops" in parsing.



