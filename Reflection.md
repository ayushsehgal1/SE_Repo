1.	Which issues were the easiest to fix, and which were the hardest? Why?
•	Ans: Easiest: removing unused import, deleting eval, replacing mutable default, switching to f-strings — small, low-risk edits.
•	Hardest: replacing a bare except safely, validating/coercing JSON data on load, and renaming public functions (needed updating call sites and preserving behavior).
2.Did the static analysis tools report any false positives? If so, describe one example.
•	Ans: No clear false positives in the final run. One borderline linter warning was "raise-missing-from" (pylint) which is stylistic — not a bug, just a suggestion to preserve exception chaining.
3. How would you integrate static analysis tools into your actual software development workflow? Consider continuous integration (CI) or local development practices. 
•	Ans: Local: editor plugins + pre-commit hooks (flake8/black/isort).
•	CI: run tests → flake8 → bandit → pylint; fail PRs on new high-severity/security findings.
•	Policy: auto-fix formatting, block new high/severe issues, allow baseline for legacy warnings.
4. What tangible improvements did you observe in the code quality, readability, or potential robustness after applying the fixes?
•	Ans; Security: removed eval → Bandit clean.
•	Robustness: input validation, safe file I/O, clearer errors on bad JSON.
•	Readability/maintainability: snake_case, docstrings, fewer footguns (no mutable defaults).
•	Measured: pylint score → 10.00/10, Bandit → 0 issues, Flake8 → no errors.
