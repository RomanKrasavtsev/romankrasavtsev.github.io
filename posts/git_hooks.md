
```
vim .git/hooks/pre-commit
#!/bin/sh

BRANCH=`git branch | grep '* ' | awk '{ print $2}'`

if [[ $BRANCH != "feature/"* ]]; then
  echo "###"
  echo "Do not forget about feature/* branch name!"
  echo "gb -M ${BRANCH} feature/${BRANCH}"
  echo "###"
fi
```
