## Learning reference
-[https://www.digitalocean.com/community/tutorials/how-to-use-git-a-reference-guide](https://www.digitalocean.com/community/tutorials/how-to-use-git-a-reference-guide)


## Changing a remote's URL
- Run in git repository 
```
git remote set-url [existing-remotename] [new-remote-url]
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
```
- Reference [https://help.github.com/articles/changing-a-remote-s-url/](https://help.github.com/articles/changing-a-remote-s-url/)

## Credential cache

- Set credential cache in local/ global git
```
git config --local credential.helper 'cache --timeout=518400'
```
- Remove credential cache from local/ global git
```
git config --local --unset credential.helper
```
- Reference: [Git Credential Cache](https://git-scm.com/docs/git-credential-cache)