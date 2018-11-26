# Git training

## How to start
Repository is public, so you pease clone it :)
```
git clone git@github.com:99stealth/git-training.git
```
or if want to use https method, then:
```
git clone https://github.com/99stealth/git-training.git
```

## 1. Add with --patch
- Go to the branch `feature/patch`
```
git checkout feature/patch
```
- You can find there file named `file_for_patch_demo.txt`. Open it for editing using any editor you like. Yes you can see `Lorem ipsum` there.
- Add something before the text, for example:
```
Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo.
```
And something after, for example:
```
Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt.
```
- Now save changes and add file with `--patch` option.
```
git add --patch file_for_patch_demo.txt
```
- Open editing mode (Press `e` and `Enter`) and delete first line from changes, save and exit
- Check status:
```
git status
```
You can see that the same file is in two stages `Changes to be committed` and `Changes not staged for commit`
- Commit your changes:
```
git commit -m "Added one line of text after the Lorem ipsum"
```
- Add the rest
```
git add file_for_patch_demo.txt
```
- Now commit:
```
git commit -m "Added one line of text before the Lorem ipsum"
```
