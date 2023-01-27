# ls
[doc](https://www.computerhope.com/unix/uls.htm)
`-l` prints
`-rw-r--r--    1 hakw    14 Jan 24 18:40 foo.sh`
`-a` shows hidden files

`ll` is an alias for `ls -al`

# source
`source ./foo.sh` is the same as `. ./foo.sh`.

ensures that the virtual environment’s variables are set within the current shell, and not in a subprocess (which then disappears, having no useful effect).

```bash
cd $(mktemp -d)
echo "export FOOO=1" >> foo.sh
chmod +x foo.sh
./foo.sh
echo $FOOO # prints nothing, var FOOO disappears after the sunprocess returns.
```

```bash
cd $(mktemp -d)
echo "export FOOO=1" >> foo.sh
chmod +x foo.sh
source ./foo.sh
echo $FOOO # prints 1, source command sets the var FOOO
```

# mktemp
`mktemp` creates a temp file
`-d` creates a temp directory

# chmod
`+x` makes file executable