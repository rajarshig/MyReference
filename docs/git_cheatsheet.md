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