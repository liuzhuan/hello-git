# How do I make Git use the editor of my choice for commit?

http://stackoverflow.com/questions/2596805/how-do-i-make-git-use-the-editor-of-my-choice-for-commits

by digitaldreamer & Ahmad Awais

If you want to set the editor only for Git, do either (you don't need both):

* Set `core.editor` in your Git config: `git config --global core.editor "vim"`
* Set the `GIT_EDITOR` environment variable: `export GIT_EDITOR=vim`

If you want to set the editor for Git and also other programs, set the standardized `VISUAL` and `EDITOR` environment variables:

```
export VISUAL=vim
export EDITOR="$VISUAL"
```
> Setting both is not necessarily needed, but some programs may not use the more-correct `VISUAL`. See [VISUAL vs. EDITOR](https://unix.stackexchange.com/questions/4859/visual-vs-editor-whats-the-difference).

For Sublime Text: Add this to the `.gitconfig`. The `--wait` is important (it allows for type text in sublime and will wait for save/close event.)

```
[core]
    editor = 'subl' --wait
```

> 'subl' can be replaced by the full path of the executable but is usually available when correctly installed.