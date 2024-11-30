## Converting and deploying MARLOWE code as JSON

+ Nested When/Case Structures
Each nested When creates a new level of nesting in the JSON
Empty When [] becomes "when": []
The nesting structure is preserved precisely

+ Role Tokens vs Addresses
Marlowe: (Role "Party")
JSON: {"role_token": "Party"}
Unlike addresses in the deposit example, roles use a different JSON structure
This is unambiguous - roles and addresses can't be confused

+ Choice Structures
*marlowe*
~~~
(Choice (ChoiceId "Price in first window" (Role "Oracle")) [Bound 0 1000000000])
~~~
becomes
*json*
~~~
{
  "case": {
    "for_choice": {
      "choice_owner": {"role_token": "Oracle"},
      "choice_name": "Price in first window"
    },
    "choose_between": [{"to": 1000000000, "from": 0}]
  }
}
~~~

Choice bounds are explicitly represented as from/to ranges
Choice owners and names are preserved in a structured format

+ Conditional Logic
*marlowe*
~~~
(If (ValueGT ...) (Let ...) (If ...))
~~~
becomes
*json*
~~~
{
  "if": {
    "value": {...},
    "gt": {...}
  },
  "else": {...}
}
~~~

Conditional structures maintain their logic flow
Comparisons (GT, LT) become explicit JSON fields
Both true and false branches are preserved

+ Variable Operations
Variable declarations use "let"/"be" structure
Mathematical operations have specific JSON representations (e.g., "minus" for subtraction)

Token representation remains consistent (token_name/currency_symbol)
All timeouts use POSIX timestamps consistently
The basic When/Case structure scales to arbitrary complexity
Close statements are consistently represented as "close"

The JSON representation is deterministic - each Marlowe construct has exactly one way to be represented
The transformation preserves all semantic information
Despite increased complexity, the patterns remain consistent with the simpler deposit example
The JSON structure makes it easier to parse programmatically while maintaining all contract logic
