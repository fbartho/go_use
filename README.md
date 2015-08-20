go_use
======

If you need to switch between versions of go for different projects, things can be a hassle. If you use homebrew, that doesn't have to be a problem.

	fbartho@fb-mbpro:~/Code/go_use$  go_use_12
	Was using go12 (go version go1.2.2 darwin/amd64)
	Unlinking /usr/local/Cellar/go12/1.2.2... 5 symlinks removed
	Linking /usr/local/Cellar/go12/1.2.2... 5 symlinks created
	Using go version go1.2.2 darwin/amd64 at /Users/fbartho/Code/gopath/go12
	fbartho@fb-mbpro:~/Code/go_use$  echo $GOROOT; echo $GOPATH
	/usr/local/Cellar/go12/1.2.2/libexec
	/Users/fbartho/Code/gopath/go12
	fbartho@fb-mbpro:~/Code/go_use$  go_use_14
	Was using go12 (go version go1.2.2 darwin/amd64)
	Unlinking /usr/local/Cellar/go12/1.2.2... 5 symlinks removed
	Linking /usr/local/Cellar/go/1.4.2... 3 symlinks created
	Using go version go1.4.2 darwin/amd64 at /Users/fbartho/Code/gopath/go
	fbartho@fb-mbpro:~/Code/go_use$  echo $GOROOT; echo $GOPATH
	/usr/local/Cellar/go/1.4.2/libexec
	/Users/fbartho/Code/gopath/go

# Installation

1. First, install the go versions you want to use. Examples: `brew install go` `brew install go12` (ignore warnings about linkage, of course they collide!)
2. Decide where you want the global go-paths for each version to be. (Edit GOPATHBASE in [go_use_fixup_env](./bin/go_use_fixup_env) for your environment). This keeps different go-versions of packages from clobbering each other.
3. Make sure to create the go-paths once you've decided. bin, pkg, src folders should be present in each.
4. Drop these scripts into a folder that is in your $PATH. (or link this folder into your PATH)
5. `echo "go" > ~/.go_ver` (this file stores the "current" choice of go version)
6. [Recommended] add the following to your bash .profile or .bash_login files. This will install the aliases to switch between versions and also load in the appropriate paths & roots into your shell's environment.
	
```
	source `which go_use_aliases`; go_use_refresh
```
