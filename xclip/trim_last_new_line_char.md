# Trim Last New Line Character
`xclip` contains a `-rmlastnl` flag (or use `-r` shorthand instead) with which you can remove the last character if it is a new line `\n` character.

This is useful to paste a selection to the command prompt without executing the line immediately.
``` shell
echo "Hello" | xclip -r
```
If the selection does not end with a new line character then this has no effect.

See `man xclip` for more details.
