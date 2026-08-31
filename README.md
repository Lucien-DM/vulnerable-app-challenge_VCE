# Code Review Activity: Secure Software Development

## What you're doing

`app.py` is a small user-management script with a number of
security vulnerabilities present. Your task is to review
it the way a developer would review a colleague's pull request, and leave
comments identifying the problems you find.

## Task 1: Code review (core task)

1. Work through the Vulnerability Checklist below against the code.
   - Check the Vulnerability Glossary at the bottom of this file if you are unsure
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
2. Either **Clone** your fork to your computer, or **edit the file directly** on
   GitHub in your fork.
3. **Create a new branch**, e.g. `review-<yourname>`.
4. Add a single marker line at the very top of `vulnerable_app.py`:
   ```python
   # Reviewed by <yourname>
   ```
   This creates a small change so GitHub has something to display in your
   pull request.
5. **Commit (and push)** your branch to your fork.
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

## Vulnerability glossary
 
Not sure what one of the vulnerabilities are? Check here to help decide whether it's
present in the code.
 
| # | Vulnerability | Definition |
|---|---|---|
| 1 | Hardcoded credentials or API keys | A password or key is written straight into the code instead of stored somewhere secure. Anyone who can read the code can read the secret. |
| 2 | Cross-site scripting (XSS) | An attacker sneaks a script into a web page so it runs in someone else's browser. It's usually used to steal login data or act as that user. |
| 3 | Missing authorisation checks | A function doesn't check whether the person calling it is actually allowed to. So anyone can trigger it, not just the intended user. |
| 4 | Insecure deserialisation | Data from an untrusted source is turned back into a program object without checking it first. An attacker can use this to run their own code. |
| 5 | Plaintext password storage | Passwords are saved or compared in plain, readable text instead of being scrambled (hashed). Anyone with access to the storage can read them directly. |
| 6 | Command injection | User input is fed into a system command without checking it. An attacker can slip in extra commands that get run along with it. |
| 7 | Missing rate limiting | There's no limit on how many times someone can try an action, like logging in. This makes it easy to guess passwords by brute force. |
| 8 | Insecure API calls | Data sent to or from an API isn't encrypted. Anyone intercepting the connection can read it, including any passwords or keys sent with it. |
| 9 | Weak or deprecated cryptography | The encryption method used is outdated and has known weaknesses. It can be broken with modern computing power, so it no longer protects the data. |
| 10 | Unvetted third-party library | Outside code is added to the project without checking where it came from or whether it's safe. It could contain bugs or malicious code. |
| 11 | Cross-site request forgery (CSRF) | A user is tricked into sending a request to a site they're logged into, without meaning to. The site can't tell it wasn't the user's real intention. |
| 12 | Missing input validation | Data entered by a user isn't checked before it's used or stored. This lets bad or unexpected input cause problems further down the line. |
| 13 | Path traversal | An attacker manipulates a file path to reach files outside the folder they should be limited to. This can expose files that should be private. |
| 14 | Hardcoded backdoor | A hidden account or shortcut is built into the code that skips normal login checks. It's often left over from testing and forgotten about. |
| 15 | Verbose error messages | Error messages reveal internal details, like file paths or system info. This gives an attacker useful clues about how the system is built. |
| 16 | No logging or monitoring | Important actions, like deleting a user, aren't recorded anywhere. If something goes wrong, there's no record of what happened or who did it. |
| 17 | SQL injection | User input is inserted straight into a database query without checking it. An attacker can change the query to read, change, or delete data they shouldn't be able to. |
| 18 | Development/production not separated | Code being tested runs on the same systems, data, or logins as the live product. A mistake made while testing can affect real users or real data. |
| 19 | Race condition | Two operations try to access the same data at the same time, and the result depends on which one runs first. This can cause data to be lost or corrupted. |
