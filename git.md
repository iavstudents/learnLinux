# Git

Git is a distributed version-control system for tracking changes in source code during software development. It is designed for coordinating work among programmers, but it can be used to track changes in any set of files. Its goals include speed, data integrity, and support for distributed, non-linear workflows. Wikipedia

License: GPLv2, LGPLv2.1, and others

Initial release: 7 April 2005; 14 years ago

Developer(s): Junio Hamano and the community

Stable release: 2.23.0 / 16 August 2019; 7 days ago

Operating system: POSIX: Linux, Windows, macOS

Original author: <b>Linus Torvalds</b>

cited from wikipedia

### Want to skip this git.md? 

RTFM about git!
https://git-scm.com/book/en/v2

## Git Basic Usage

1. Git add [file/directory]

```
git add .
```

. means all

2. Git Commit

```
git commit
```

or write comment directly by adding -m parameter

```
git commit -m "Your Comment Log Here"
```

or you want to sign by adding -S

```
git commit -S -m "Your Comment Log"
```



3. Git Push(Optional)

```
git push
```

```
git push origin master
```

git push used to push our code to online repo such as github, gitlab, etc.

but we must add a remote to there first, which is by

4. Git Remote Add

```
git remote add [url-to-repo]
```


## Git Aliasing

What is Aliasing?

well it's looks like this,

instead of writing

```
git log --oneline --relative-date --shortstat --decorate --all
```

we can just write, for example,

```
git plog
```

to get same result as above

how? that's what aliasing do!

we can do aliasing by using git config command,

```
git config --global alias.plog log --oneline --relative-date --shortstat --decorate --all
```

or as a rock guy, you will edit .gitconfig file directly

```
[alias]
	plog = log --oneline --relative-date --shortstat --decorate --all
```

and so so,

you can config your own aliases!

like using your girlfriend name to commit or push or add or etc...

```
git [yourgirlfriendname]
```

```
[alias]
  [yourgirlfriendname] = commit -S -m
```

i think it's worth instead of making aliases on your shell environment which is globally, so it's just locally git

## Sign Commit with GPG Key

1. Make GPG Key
```
gpg --full-generate-key
```
2. Check GPG Key List
```
gpg --list-secret-keys --keyid-format LONG
```
3. Paste GPG Key to a file

From the list of GPG keys, copy the GPG key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:

```
$ gpg --list-secret-keys --keyid-format LONG
```
```
/Users/hubot/.gnupg/secring.gpg

sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]

uid                          Hubot 

ssb   4096R/42B317FD4BA89E7A 2016-03-10
```

Paste the text below, substituting in the GPG key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:

```
$ gpg --armor --export 3AA5C34371567BD2 >> gpg.md
```
and then open the file gpg.md and you will see the gpg key which is looks like below, ehm, not looks like it, but, it's the pseudo

-----BEGIN PGP PUBLIC KEY BLOCK----- 

GPG Keys

-----END PGP PUBLIC KEY BLOCK-----


4. Enable GPG TTY(Ehm, the passphrase input)

- bash,zsh
```
export GPG_TTY=$(tty)
```
- fish
```
set -x GPG_TTY (tty)
```
5. Done? No! add gpg to gitconfig

```
git config --global user.signingkey [yourgpgkey]
```

example 

```
git config --global user.signingkey 3AA5C34371567BD2
```

6. Addition

All commit must signed

```
git config --global commit.gpgsign true
```

so your commit will always signed with gpg

## Git Expert

1. Git checkout
2. Git stash
3. More git command added later hehe

## HAPPY GITING!
