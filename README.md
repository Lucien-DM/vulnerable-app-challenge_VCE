# Code Review Activity: Secure Software Development

## What you're doing

`app.py` is a small user-management script with a number of
security vulnerabilities present. Your task is to review
it the way a developer would review a colleague's pull request, and leave
comments identifying the problems you find.

## Task 1: Code review (core task)

1. Work through the Vulnerability Checklist below against the code.
2. For each item, decide whether it is present in this code.
3. If it is present, note the line(s) where it occurs and briefly explain
   the risk it creates.
4. If it is not present, be ready to explain why you ruled it out — not
   every item on this list applies to this code.

## Vulnerability checklist

| # | Vulnerability | Present? | Line(s) | Notes / risk |
|---|---|---|---|---|
| 1 | Hardcoded credentials or API keys | | | |
| 2 | Cross-site scripting (XSS) | | | |
| 3 | Missing authorisation checks on sensitive functions | | | |
| 4 | Insecure deserialisation (e.g. `pickle` or `eval`) | | | |
| 5 | Plaintext password storage | | | |
| 6 | Command injection | | | |
| 7 | Missing rate limiting on login attempts | | | |
| 8 | Insecure API calls (no encryption in transit) | | | |
| 9 | Weak or deprecated cryptographic algorithm | | | |
| 10 | Unvetted third-party library use | | | |
| 11 | Cross-site request forgery (CSRF) | | | |
| 12 | Missing input validation | | | |
| 13 | Path traversal vulnerability | | | |
| 14 | Hardcoded backdoor/bypass account | | | |
| 15 | Verbose error messages or stack traces exposing internal details | | | |
| 16 | No logging or monitoring of admin actions | | | |
| 17 | SQL injection | | | |
| 18 | Development and production environments not separated | | | |
| 19 | Race condition on shared file access | | | |

## Task 2: Submit your review via GitHub Pull Request

1. **Fork** this repository to your own GitHub account.
2. **Clone** your fork to your computer, or edit the file directly on
   GitHub in your fork.
3. **Create a new branch**, e.g. `review-<yourname>`.
4. Add a single marker line at the very top of `vulnerable_app.py`:
   ```python
   # Reviewed by <yourname>
   ```
   This creates a small change so GitHub has something to display in your
   pull request.
5. **Commit and push** your branch to your fork.
6. On GitHub, open a **Pull Request** from your branch back to this
   repository's `main` branch.
7. On your PR page, open the **"Files changed"** tab. This shows the code
   with line numbers down the side.
8. Hover over any line and click the blue **`+`** that appears to leave a
   comment on that specific line. You can comment on any line in the
   file, not just the one you changed.
9. For every vulnerability you identified, leave a comment on the
   relevant line. In each comment, reference the checklist number and
   briefly explain the risk, e.g.:
   > **#5 – Plaintext password storage.** Passwords are stored and
   > compared as plain text with no hashing, so anyone with access to
   > `users.txt` can read every password directly.
10. Use **"Start a review"** as you add comments, then click
    **"Finish your review"** once you're done so all your comments are
    submitted together.

## Task 3: Extension — fix it

If you finish early:

1. Create a second branch, e.g. `fix-<yourname>`.
2. Rewrite `vulnerable_app.py` to address as many of the vulnerabilities
   you identified as you can.
3. Open a second Pull Request with your fixed code.
4. In the PR description, list which checklist items each change
   addresses.
