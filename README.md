## Quick start run on kind cluster using GitHub repo

### Install kind:

https://kind.sigs.k8s.io/docs/user/quick-start/#installation

### Create kind cluster:

```
kind create cluster
```

### Fork and clone the repository

```
git clone git@github.com:my_github_username/kind-fluxcd-test.git
```

### Remove flux-system resources from original repository

- Remove `clusters/dev/flux-system` folder
- Stage, commit and push

Flux will generate new files and commit it after it's deployed

### Create GitHub PAT token:

https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

- With repo access

### Set the PAT token as environment variable

powershell
```pwsh
$env:GITHUB_TOKEN='my_pat_token'
```

bash
```sh
export GITHUB_TOKEN='my_pat_token'
```

### Install flux and initialize:

https://fluxcd.io/docs/installation/

powershell
```pwsh
flux bootstrap github \
  --owner=my_github_username \
  --repository=kind-fluxcd-test \
  --path=clusters/dev \
  --personal
```

bash
```sh
flux bootstrap github `
  --owner=my_github_username `
  --repository=kind-fluxcd-test `
  --path=clusters/dev `
  --personal
```