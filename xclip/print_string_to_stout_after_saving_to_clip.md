# Print Content To Standard Out After Saving To Clip
`xclip` contains a `-f` flag that allows you to get the string passed to xclip from standard in and pass them to standard out. This is useful for piping the string further along.
``` shell
echo "String to put in clip" | xclip -i -f | ...
```

This is especially useful because you can pipe the string back into xclip to save the string in more than one selection.
``` shell 
echo "String to put in clip" | xclip -i -selection secondary -f | xclip -i -selection clipboard
````

See `man xclip` for more details.
