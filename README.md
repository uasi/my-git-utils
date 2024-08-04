# my-git-utils

A collection of my little utility scripts to work with Git repositories.

## git-exec-if-changed

`git-exec-if-changed` executes a given command if specified paths in a repository have changed since a specified commit.
The `--since-last-exec` option is particularly useful: it records the revision when the command was last executed
and only runs the command if paths have changed since that point.


```
% git pull

% git exec-if-changed --verbose --path package-lock.json --since-last-exec=tmp/.last-npm-i -- npm install
exec-if-changed: changed since (root)
# exec npm install...

% git pull

% git exec-if-changed --verbose --path package-lock.json --since-last-exec=tmp/.last-npm-i -- npm install
exec-if-changed: not changed since 30a87913a60ac47deb55c1588d68e0e89f2cabf6
```

See [git-exec-if-changed.md](./git-exec-if-changed.md) for more information.

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

## git-unkeep

`git-unkeep` recursively searchs for `.gitkeep` files in the work tree,
and if a directory containing a `.gitkeep` file has any entries other than the `.gitkeep` file itself,
removes the `.gitkeep` file from that directory.

`.gitkeep` is an unofficial convention to check-in otherwise empty directories.

```
% git unkeep
rm 'db/migrations/.gitkeep'
rm 'resources/.gitkeep'
```

## See also

- [`uasi/gh-blame-pr`](https://github.com/uasi/gh-blame-pr): A GitHub CLI extension to open the most recent pull request that modified the specified file.
