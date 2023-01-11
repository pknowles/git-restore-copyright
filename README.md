# git-restore-copyright

A small script to search for and replace copyright differences between a given
commit and the current state of the git working directory.

## Dependencies

pip install --user gitpython
pip install --user pydriller # for "history" option

## Usage

```
usage: git-restore-copyright [-h] [-n] [-l [LINES]] [-v] [--expand-range] {restore,undo,history} commit

Mass-restore copyrights in a git repository

positional arguments:
  {restore,undo,history}
                        Either "restore" copyright year(s) from this commit, "undo" its changes or replace them using the date from their first git
                        "history" commit.
  commit                Commit-ish to "restore" from or "undo". Only checks files indexed at this commit for "history".

options:
  -h, --help            show this help message and exit
  -n, --dry-run         Print the replacements that would have been made but do not modify the files.
  -l [LINES], --lines [LINES]
                        Number of lines to search in file headers for a copyright notice with a year
  -v, --verbose         List the files that are being inspected
  --expand-range        Rather than just restore "2023" to the original year "2014", replace it with a range covering all years, e.g. "2014 - 2023".
```

**Example**

````
git-restore-copyright restore 7ff7a935 --verbose --dry-run
````
