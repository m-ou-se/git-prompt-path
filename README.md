# git-prompt-path

Display git information next to every path component in your prompt.

Example output:

  ![~/src/project(master+1)/foo*/bar/baz+%/submodule(release-1.2=)%/fizz/buzz][1]

Note how the branch names of both the project and the submodule are
visible, and how the state of the index and worktree is visible at every
directory.

The status symbols are the same as used by `__git_ps1` from [`git-prompt.sh`][2]:

 - `+` Changes in index.
 - `*` Changes in working tree.
 - `%` Untracked files.

## Screenshot

![screenshot][3]

## Usage examples

First source both [`git-prompt.sh`][2] from git/contrib,
and `git-prompt-path.sh` from this repository:

    source ~/.../git-prompt.sh
    source ~/.../git-prompt-path.sh

And then for `zsh`:

    setopt prompt_subst
    PROMPT='$(git_prompt_path)$ '


Or for `bash`:

    function update_ps1 { PS1="$(git_prompt_path)\$ " }
    PROMPT_COMMAND=update_ps1


These will use the default colours. To use it without colour, call
`git_prompt_path` with a format string without colour codes:
  `$(git_prompt_path "%s%s")`

Alternatively, to use your own colours, put them in the format string:
  `$(git_prompt_path "...%s...%s...")...`
Make sure to surround the colour codes with the right escape sequences for
your shell. (`\[` and `\]` for bash, `%{` and `%}` for zsh. Note that the `%`s need to
be escaped inside the format string with another `%`.)

[1]: https://raw.githubusercontent.com/m-ou-se/git-prompt-path/screenshot/example-output.png
[2]: https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh
[3]: https://raw.githubusercontent.com/m-ou-se/git-prompt-path/screenshot/screenshot.png

## License

The code is licensed under the 2-clause BSD license.
See the header of `git-prompt-path.sh`.

### Authors

- Maarten de Vries \<maarten@de-vri.es\>
- Mara Bos \<m-ou.se@m-ou.se\>
