# Grammars

This repository contains open source versions of commonly used grammars and their delegates.

## Syntax

| Operator | Characters | Description |
| -------- | ---------- | ----------- |
| AND | ( ) | Spoken in sequence |
| OR | [ ] | Alternatives |
| OPT | ? | Optional word or grammar |
| LOOP | + | One or more of |
| KLEENE | * | Zero or more of |

NULL productions are disallowed, meaning a grammar must map to at least one word.
To effect a NULL, use the OPT or KLEENE operators, but the grammar containing it
must still produce at least one word.

