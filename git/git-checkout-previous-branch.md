# Use `git checkout -` to checkout the previous branch

Instead of having to remember the last branch name (or, God forbid, the last commit hash), we can simply use `git checkout -`

The single dash argument `-` in this command is synonymous to `@{1}`, a usage of the `@{-N}` syntax, which refers to the N-th last branch/commit checked out using "git checkout" operation. Effectively turning this command into "checkout the (1st) last branch/commit checked out using the "git checkout" operation.