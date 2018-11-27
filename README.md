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

## 2. Use stash
- Go to the branch `feature/stash`
```
git checkout feature/stash
```
- You can find one file there named `file_for_stash_demo.txt`. Open it and check what is inside
- Create another branch `feature/stash_v2`:
```
git checkout -b feature/stash_v2
```
As you can see you are inside the newly created branch
- Open the file `file_for_stash_demo.txt` and change version from `1.0.0` to, let's say `1.0.1`, save and exit
- Add changes
```
git add file_for_stash_demo.txt
```
- Commit changes
```
git commit -m "Increased version"
```
- Push changes to remote server
```
git push origin feature/stash_v2
```
- Now go back to branch `feature/stash`
```
git checkout feature/stash
```
- Add something to file `file_for_stash_demo.txt` in the bottom line. For example:
```
File version 1.0.0
Something important
```
- Let's imagine that in the middle of something you remembered that you need to make something else in the `feature/stash_v2`. So you decided to go back to that branch and make your changes
```
git push origin feature/stash_v2
```
Looks like you are in the trouble, as you see something like this:
```
error: Your local changes to the following files would be overwritten by checkout:
	file_for_stash_demo.txt
Please commit your changes or stash them before you switch branches.
Aborting
```
- No worries, let's improve. Now we are going to use `stash`
```
git stash add "Something important"
```
- Now try to checkout again
```
git push origin feature/stash_v2
```
- Check what is in your `stash`
```
git stash list
```
- Ok now you can go back to your initial branch and unstash your changes
```
git checkout feature/stash
git stash pop
```
