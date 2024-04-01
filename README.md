# Info
This is a forked version of KeyDB Helm Chart by Enapter [https://github.com/Enapter/charts].
Since the repository was by the owner on Jun 6, 2023, it is now read-only and I 
was missing some features, I have decided to do a fork.


## New KeyDB release example

### Package new release in .tgz

```cli
helm package ./keydb/ --destination ./.deploy/
```

### Upload the release to Github

Using [Helm Chart Releaser](https://github.com/helm/chart-releaser)

```cli
helm-cr upload --skip-existing --config ~/.cr.yaml
```

### Update index.yaml

```cli
git checkout gh-pages
helm-cr index --config ~/.cr.yaml -i ./index.yaml -c https://enapter.github.io/charts/
```

```cli
cr upload --owner <owner> --git-repo <repo_name> --packages-with-index --token <token> --push --skip-existing

cr index --owner <owner> --git-repo <repo_name>  --packages-with-index --index-path . --token <token> --push
```