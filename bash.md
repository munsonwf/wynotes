# Bash

Get drangerous in bash.

## What is Bash

## Common Bash Commands

### ls

**`ls -l` output**

The `-l` flag indicates a list in long format.

```
$ ls -l

-rw-r--r--  1 wyatt  staff  721 May  2 19:46 bash.md
^           ^ ^      ^      ^   ^            ^
A           B C      D      E   F            G


```

Key:

- A: File permissions
- B: Links
- C: Owner
- D: Group
- E: File size
- F: Date
- G: File name

A. File Permissions

```
-rw-r--r--
FUUUGGGOOOS
```

F = File type flag  
U = User/owner
G = Group members
O = All others
S = Alternative access (null if blank)

**B. Link Count**

What constitutes a link here varies.

**C. Owner Account**

**D. Group**

**E. File sieze**

Again, depends on the filesystem. In OSX, it refers to bytes.

**F. Date**
