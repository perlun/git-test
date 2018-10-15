# git-test
Test repo for overwriting ignored files

## How to reproduce

```
$ git init
$ touch foo.txt
$ nano foo.txt 
$ git add foo.txt 
$ git commit -m 'Add foo.txt'
[master (root-commit) 8ef05cb] Add foo.txt
 1 file changed, 1 insertion(+)
 create mode 100644 foo.txt
$ git checkout -b dev
Switched to a new branch 'dev'
$ git mv foo.txt foo.bar
$ git commit -m "Rename foo.txt -> foo.bar"
[dev 4c55c9b] Rename foo.txt -> foo.bar
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename foo.txt => foo.bar (100%)
$ echo 'my local foo.txt' > foo.txt
$ echo foo.txt > .gitignore
$ git commit -m "Add .gitignore"
[dev 4c16acb] Add .gitignore
 1 file changed, 2 insertions(+)
 create mode 100644 .gitignore
$ git checkout master # This will silently overwrite the local foo.txt file
```
