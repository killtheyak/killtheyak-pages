title: use submodules in git
updated: 2015-10-10 11:11:33
description: Helpful commands for working with git submodules.
os: [macosx, linux, windows]
tags: [git]
deps: []
contributors: ["http://www.github.com/anschwa"] 

How to use submodules in `git`.

# Cloning Repository with Submodules

There are two ways to do this:

First, clone the repository without fetching the submodule's files: 
```
git clone <repository>
```

Then, fetch all the submodule data:
```
git submodule init
git submodule update
```

Or, you can simply do this all at once with:
```
git clone --recursive <repository>
```

# Removing Submodule

Taken from: [David Walsh's Remove a Submodule within git ](http://davidwalsh.name/git-remove-submodule)

1. Delete the relevant section from the `.gitmodules` file.  The section would look similar to:

```
[submodule "vendor"]
	path = vendor
	url = git://github.com/some-user/some-repo.git
```

2. Stage the `.gitmodules` changes via command line using:
```
git add .gitmodules
```

3. Delete the relevant section from `.git/config`, which will look like:

```
[submodule "vendor"]
	url = git://github.com/some-user/some-repo.git
```

4. Run:
```
git rm --cached path/to/submodule
```
Don't include a trailing slash, that will lead to an error.

5. Run:
```
rm -rf .git/modules/submodule_name
```

6. Commit the change:

7. Delete the now untracked submodule files
```
rm -rf path/to/submodule
```
