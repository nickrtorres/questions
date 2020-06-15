- Increment a list of numbers? `<CTRL-V>g<CTRL-A>` will create a sequence of
  increasing numbers e.g. before:
  ```
  1.
  1.
  1.
  1.
  ```
  after:
  ```
  1.
  2.
  3.
  4.
  ```
- Execute an `ex` command from the shell? The following command removes
  trailing whitespace from <FILE> without entering `vim`.
  ```
  % vim -e -c '%s/\s\+$//g' -c 'wq' <FILE>
  ```
