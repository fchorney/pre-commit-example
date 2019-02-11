# pre-commit example

## Problem

When a pre-commit script is set up to modify a file before commit, the diff in the commit editor displays the non modified diff (Assuming commit --verbose).

## Expected

It would be expected that the diff in the commit editor would have the diff after the pre-commit hook has run

## Reproduce

Hook up the git hook

```
cd .git/hooks
ln -s ../../hooks/pre-commit .
```

Modify test.py in any way, as the pre-commit hook will be run when a .py file is modified and added.

```
vim test.py
# Modify test.py somehow
git add test.py
git commit --verbose
```

The pre-commit script is setup to add the line `extra thing` to the end of the file to be committed (in this case it's test.py).
You will notice that this `extra thing` doesn't show up in the diff that the commit editor shows you.
