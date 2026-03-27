# AI vs. Human Code: Feature Engineering Matrices

This document outlines the multidimensional feature engineering matrices used to distinguish between AI-generated and human-written code across multiple programming languages. The features are divided into cross-language human micro-habits and language-specific ecosystem imprints.

## Table 1: Cross-Language Human Micro-Habits

These features transcend programming language boundaries, capturing physical typing habits, emotional fluctuations, and imperfections caused by IDE friction or developer fatigue.

| Category / Perspective | Feature Variable Name(s) | Core Explanation (AI vs. Human Discrepancy) |
| :--- | :--- | :--- |
| **Spelling & Emotions** | `typo_density`, `micro_typo_density` | **Typographical Errors**: Captures manual typing mistakes (e.g., `lenght`, `recieve`). LLMs rarely make physical spelling errors. |
| | `informal_tag_density`, `micro_informal_tag_density`| **Emotional & Informal Tags**: Human-specific venting or informal comments (e.g., `wtf`, `shit`, `hack`). AI outputs are strictly neutral and aligned. |
| **Heuristic Debugging** | `console_usage`, `print_debug_density` | **Console Dominance**: Humans heavily rely on meaningless strings (e.g., `print("111")`) to trace execution flow; AI tends to omit debug stubs or uses standardized loggers. |
| | `simple_function_names`, `human_var_density` | **Casual Placeholders**: Humans favor `test`, `demo`, `tmp`, `foo` for verification logic; AI generates highly descriptive and semantically complete identifiers. |
| **Formatting Friction** | `crowded_operator_density` | **Crowded Operators**: Humans typing single lines often omit spaces (e.g., `a==b`); AI maintains standard spacing globally. |
| | `missing_space_after_kw` | **Missing Keyword Spaces**: Human manual typing frequently misses spaces (e.g., `if(` vs. standard `if (`). |
| | `brace_style_inconsistency` | **Brace Style Fluctuation**: Mixing same-line `{` and next-line `{`, reflecting multi-file copy-paste fatigue; AI strictly locks its style per generation. |
| | `mixed_indentation_ratio` | **Mixed Indentation**: Mixing Tabs and Spaces (often a copy-paste hangover); AI formatting exhibits near-perfect contextual consistency. |
| | `comma_missing_space_ratio` | **Comma Space Omission**: Formatting flaws like `a,b` instead of standard `a, b`. |
| | `trailing_whitespace_ratio` | **Trailing Whitespace**: Humans easily leave extra spaces at line ends; AI output formatting is clean and trimmed. |
| | `mixed_quotes_ratio` | **Mixed Quotes**: Arbitrary switching between single and double quotes; AI maintains a uniform style. |
| **Laziness & Remnants** | `err_empty_catch_ratio`, `empty_except_ratio` | **Silent Exception Swallowing**: Humans often write empty Catch/Except blocks to suppress compiler errors; AI typically retains stack traces or logging. |
| | `commented_code_ratio` | **Deprecated Code Remnants**: Humans use `//` to backup old logic during refactoring; AI outputs the final "burn-after-reading" state. |
| | `magic_numbers`, `ai_magic_numbers` | **Hardcoded Magic Numbers**: Humans directly hardcode configurations; AI is more likely to extract them as named constants. |
| | `multiple_declaration_ratio` | **Multiple Declarations**: Human laziness (`int a, b;`); AI strictly follows the one-declaration-per-line convention. |
| | `redundant_parens_ratio` | **Redundant Parentheses**: Humans modifying logic often leave nested leftovers `((a+b))`; AST-based AI generation prevents this. |
| **Copy-Paste Artifacts**| `consecutive_identical_call_ratio`, `repetitive_patterns` | **Consecutive Identical Calls**: The human hardcoding habit of "copy-paste-modify args"; AI prefers algorithmic refactoring like loops or maps. |
| **AI-Specific Residue** | `has_ai_generation_tag` | **Prompt Residue**: Captures generator-specific filler text accidentally left in the code. |
| | `over_documented` | **Over-Documentation**: AI, fine-tuned as an "explainer," often generates excessive JSDoc/Docstrings for trivial functions. |

## Table 2: Language-Specific Features

These features target the underlying constraints of specific compilers, framework evolution histories, and unique subcultures like the Competitive Programming (CP) community.

| Language | Feature Variable Name | Core Explanation (AI vs. Human Discrepancy) |
| :--- | :--- | :--- |
| **C/C++** | `yoda_condition_ratio` | **Defensive Programming**: Old-school geek habit `NULL == p` to prevent assignment errors; AI uses the natural syntax `p == NULL`. |
| | `cp_macro_shortcuts`, `has_bits_stdcxx`, `fast_io_magic` | **CP Black Magic Suite**: Universal headers, IO desynchronization, `pb/sz` macros. Pure Competitive Programming human imprints. |
| | `ptr_arithmetic_density`, `bitwise_op_density`| **Low-Level Geek Compression**: Using `*ptr++` or bitwise operations instead of standard logic for micro-optimizations. |
| | `c_style_cast_density` vs `cpp_style_cast_density`| **Cast Style**: Humans lazily use C-style `(int)x`; modern AI formally adheres to `static_cast<int>(x)`. |
| | `modern_cpp_keyword_density`, `smart_pointer_density`| **Modern C++ Norms**: AI strictly follows C++11/14/17 norms (`constexpr`, `unique_ptr`); humans often retain legacy practices. |
| | `vertical_decl_ratio` | **System-Level Formatting**: Kernel source style with forced line breaks for macros, return types, and function names. |
| | `endl_vs_newline_ratio` | **Line Break Habits**: Beginners overuse `std::endl`; advanced humans and AI prefer `\n` to avoid buffer flushes. |
| **Java** | `cp_scanner_density` vs `cp_bufferedreader_density`| **CP IO Compromises**: Beginners use slow `Scanner`, while CP veterans stack verbose `BufferedReader` wrappers. |
| | `cp_math_density`, `cp_arrays_density` | **Procedural Paradigm Residue**: High-frequency utility class calls in strict OOP, indicating a human translating algorithmic logic from C. |
| | `lambda_density`, `stream_density` | **Modern Syntax Proficiency**: Humans often polarize between giant `for` loops and extreme one-line `.stream()`; AI balances both. |
| | `class_density`, `interface_density`, `annotation_density`| **OOP Rigor**: AI tends to generate skeleton structures with rigidly separated interfaces and complete annotations (e.g., `@Override`). |
| **JavaScript**| `modern_variable_ratio` | **Declaration Epochs**: Human legacy codebases are plagued with `var`; AI outputs are heavily fine-tuned toward `let/const`. |
| | `micro_loose_eq_ratio` | **Loose Equality Crisis**: Humans lazily abuse `==`; AI almost exclusively uses strict equality `===` to avoid implicit type coercion bugs. |
| | `destructuring_density`, `spread_operator_density`| **Modern Syntactic Sugar**: AI utilizes destructuring and spread operators (`...`) highly proficiently and uniformly. |
| | `cp_bitwise_math_floor_density` | **Bitwise Floor Truncation**: Humans use `~~x` instead of `Math.floor()` for performance. |
| | `cp_short_circuit_call_density` | **Short-Circuit Abuse**: Extreme lazy writing replacing `if` statements with `a && a.do()`. |
| **Python** | `comprehension_nesting_density` | **Over-Nested Comprehensions**: Human geeks write 2-3 level nested list comprehensions to show off; AI prefers single-level readability. |
| | `cp_sys_recursion_density`, `cp_fast_io_density` | **System-Level Limit Bypasses**: CP humans writing DFS always expand recursion limits (`sys.setrecursionlimit`); AI avoids altering system configurations. |
| | `type_hint_density` | **Type Hint Rigor**: Humans often code "typeless" scripts; AI frequently outputs complete `-> type` annotations. |
| | `dataclass_or_pydantic_density` | **Modern Encapsulation**: AI proficiently uses `@dataclass`; humans sometimes still handwrite verbose `__init__` methods. |
| **TypeScript**| `ts_any_usage_pattern` | **Mindless "Any" Escape**: The ultimate human compromise to abandon strict type inference (`: any`). |
| | `micro_as_any_abuse_density` | **Brute-Force Assertion Abuse**: Humans force `as any` to silence the compiler; AI elegantly resolves this with Type Guards or generics. |
| | `micro_non_null_abuse_density` | **Non-Null Assertion Carnival**: Humans spam `val!`; AI is stricter, preferring optional chaining `val?.`. |
| | `micro_old_assertion_density` | **Antique Assertions**: `<Type>value` syntax copied from old StackOverflow posts, violating modern TSX compatibility norms. |
| | `ts_generic_nesting_depth`, `ts_generic_constraint_ratio`| **Deep Type Gymnastics**: Captures nested generics (`<T extends ...>`); AI usually exhibits deeper and stricter type deduction capabilities. |
| | `ts_access_modifier_density`, `ts_readonly_ratio` | **OOP Modifiers**: Pure JS-to-TS humans often forget `private` and `readonly`; AI complies with full class encapsulation norms. |
| | `ts_decorator_density` | **Framework Ecosystem Imprints**: Statistical density of `@` decorators, distinguishing Angular/NestJS enterprise ecosystem marks. |
| | `cp_bigint_literal_density`, `cp_mod_constant_flag` | **Large Integer CP Features**: Long BigInt suffixes or classic modulo constants (e.g., `1000000007n`), extremely rare in standard enterprise engineering. |
