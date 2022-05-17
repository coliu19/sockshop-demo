# Guide

Download the cli locally and you can try the demo flow locally.
```
./demo.sh
```

v0.0-rev1: raw spec
v0.0-rev2: perfect spec
v0.1-rev1: add some violations against perfect spec
v0.1-rev2: fix all the issues in v0.1-rev1

## Trigger workflow

1. Change the catalogue.json in openapi folder by copying the same files in other version folders.
```
cp v0.1-rev1/catalogue.json openapi/
```
2. Show the diff.
```
git diff
```
3. Commit the change. This will trigger the analyze and diff check.
```
git add openapi/catalogue.json
git commit -m "add delete catalogue api"
git push origin master
```
4. Change the tag in ./trigger-ci.sh to v0.1-1, run the shell script, to trigger upload. UI will show the result as well.
```
./trigger-ci.sh
```
5. Fix the broken spec by coping the one from v0.1-rev2.
```
cp v0.1-rev2/catalogue.json openapi/
```
6. Show the diff.
```
git diff
```
7. Commit the change. This will trigger the analyze and diff check.
```
git add openapi/catalogue.json
git commit -m "fix catalogue api"
git push origin master
```
8. Change the tag in ./trigger-ci.sh to v0.1-2, run the shell script, to trigger upload. UI will show the result as well.
```
./trigger-ci.sh
```

## Useful commands


```
apiregistryctl diff v0.1-rev1/catalogue.json -s catalogue --version 0.0 --revision 2 -o text
```
