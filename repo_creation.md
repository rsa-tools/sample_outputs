# how this repo as been created

### Clone old and new empty repo

```
git clone git@depot.biologie.ens.fr:rsat ens_rsat_sample_outputs
git clone git@github.com:rsa-tools/sample_outputs.git github_sample_outputs
```

### Use filter-repo to filter the directory

```
cd ens_rsat_sample_outputs
git remote remove origin # no needed, but it is more secure (should not be done if we want to update this repo)
git filter-repo --subdirectory-filter public_html/sample_outputs --force --preserve-commit-hashes
```
See https://github.com/newren/git-filter-repo


### Get the commit in the new repo
```
cd ..
cd github_sample_outputs
git remote add ens_updated  ../ens_rsat_sample_outputs
git fetch ens_updated
git merge ens_updated/master -s recursive -X theirs
```


### Push in new repo on main branch
```
git push -u -f origin master
```
