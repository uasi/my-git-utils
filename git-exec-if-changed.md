# git-exec-if-changed

`git-exec-if-changed` executes a given command if specified paths in a repository have changed since a specified commit.

## Usage

```
git-exec-if-changed [<options>] [--] <cmd>...
```

## Options

- `-p <path>`, `--path=<path>`: Path to test if changed (can be specified multiple times)
- `-s <commit>`, `--since=<commit>`: Find changes since `<commit>` (use empty string for the root commit)
- `-S <history-file>`, `--since-last-exec=<history-file>`: Behave as `--since=$(cat <history-file>)` if it exists; write the current revision to `<history-file>` before exec
- `-v`, `--verbose`: Enable verbose output

## Examples

Execute a command if a specific file has changed since the last commit:

```
% git exec-if-changed -p path/to/file.txt -s HEAD^ -- echo "File changed"
```

Run tests if any files in the `src` directory have changed since a specific commit:

```
% git-exec-if-changed -p src -p lib -s abc1234 -- npm run test
```

Execute a build command if changes occurred since the last execution:

```
% git-exec-if-changed -p src -p lib -S tmp/.last-build -- make build
```
