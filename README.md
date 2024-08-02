# my-git-utils

A collection of my little utility scripts to work with Git repositories.

## git-guess-default-branch

`git-guess-default-branch` guesses the default branch name.

Git repositories usually have a default branch, but its name varies depending on the repository, such as master, main, or develop.
This command would be useful when you want to manipulate the default branch without specifying the branch name.

```
% git branch
* feature/foo
  master
  release

% git guess-default-branch
master
```

See [git-guess-default-branch.md](./git-guess-default-branch.md) for more information.
