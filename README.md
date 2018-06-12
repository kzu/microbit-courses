# microbit-courses

Courses with content from Microsoft/pxt-microbit


## updating from upstream

The `courses/en` folder comes staight from https://github.com/Microsoft/pxt-microbit/tree/master/docs/courses.
In order to update it and preserve its history, follow these steps:

```
# Add remote first time you do this only
git remote add -f microbit git@github.com:Microsoft/pxt-microbit.git
# If remote already added, fetch instead
git fetch microbit

git checkout -b staging microbit/master
git subtree split -P docs/courses -b docs-courses
git checkout master
git rm -rf courses/en
git commit -m "Prepare for update" courses/en
git subtree add -P courses/en docs-courses
git branch -D docs-courses staging
git push
```

Updating static images:

```
git checkout -b staging microbit/master
git subtree split -P docs/static/courses -b static-courses
git checkout master
git rm -rf static/en
git commit -m "Prepare for update" static/en
git subtree add -P static/en static-courses
git branch -D static-courses staging
git push
```
