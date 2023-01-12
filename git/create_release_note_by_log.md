# Memo (Should be better further)

## Reference
- [Sample code](https://stackoverflow.com/questions/8136178/git-log-between-tags)

## Script
```
export VERSION=$(git tag --sort=-committerdate | head -1)
export PREVIOUS_VERSION=$(git tag --sort=-committerdate | head -2 | awk '{split($0, tags, "\n")} END {print tags[1]}')
export CHANGES=$(git log --pretty="- %s" $VERSION...$PREVIOUS_VERSION)
printf "# Release notes (\`$VERSION\`)\n\n## Changes\n$CHANGES\n\n## Metadata\n\`\`\`\nThis version -------- $VERSION\nPrevious version ---- $PREVIOUS_VERSION\nTotal commits ------- $(echo "$CHANGES" | wc -l)\n\`\`\`\n" > release_notes_$VERSION.md
```

## Q&A
### How to set& check your environment vairalbes ?
- [link](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-linux)

#### set
```
export <KEY>=<VALUE>
```
#### check
```
printenv <variable name>
```
