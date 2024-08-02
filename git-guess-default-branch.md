# git-guess-default-branch

`git-guess-default-branch` prints the guessed default branch name of the current repository.

## Usage

```
git guess-default-branch
```

## Examples

```
% git branch
* feature/foo
  master
  release

% git guess-default-branch
master

% git config set guessDefaultBranch.override release

% git guess-default-branch
release
```

## Configuration

- `guessDefaultBranch.fallback`: This value will be used as the default branch name when other checks failed. Default: the value of `init.defaultBranch` if it is set, otherwise `master`.
- `guessDefaultBranch.override`: If set, this value will be used as the default branch name, bypassing other checks.
- `guessDefaultBranch.wellKnown`: A space-separated list of branch names to check for existence. If multiple branches are found, the name specified earlier in the list is used. Default: `master main develop trunk`.
