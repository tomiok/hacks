### Moves pointer back to previous HEAD
```bash
git reset --soft HEAD@{1}
```

### Push specific tag into remote
```bash
git tag -a v0.1.0 -m "Some message"
git push origin v0.1.0
```

### To solve tag/branch name clashes, use:
```bash
git push origin refs/tags/v0.1.0
```
### Redploy to heroku when no code changes
```bash
git commit --allow-empty -m "{message here}"
git push heroku master
```

### Delete a tag
```bash
git tag -d v0.1.0-SAAS-213
```
