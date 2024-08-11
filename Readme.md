Use kubectl to get **really** all items in the cluster or in a namespace.

# Usage

Get everything in a cluster:

```bash
kubectl get-all
loading 179 apis in 10 threads ...
NAME                               STATUS   VOLUME
persistentvolumeclaim/test-claim   Bound    pvc-123
> ...
```

Get everything in a namespace:
```bash
kubectl get-all -n foo'
> ... lots of output
```

- Passes along all options like `-l` / `--as` / `--context` etc to `kubectl`
- Supports parallel fetching of many apis with `--parallel 10` (default)

# Install

## Option A: via `krew`

```bash
kubectl krew install --manifest-url https://raw.githubusercontent.com/grosser/kubectl-get-all/master/krew.yaml
```

## Option B: copy into your /usr/local/bin folder

```bash
sudo wget https://raw.githubusercontent.com/grosser/kubectl-get-all/master/kubectl-get-all -O /usr/local/bin/kubectl-get_all
sudo chmod +x /usr/local/bin/kubectl-get_all
```

## Option C: use from checkout

```bash
git clone git@github.com:grosser/kubectl-get-all.git
cd kubectl-get-all && ./kubectl-get-all
```

# Alternatives

- [ketall](https://github.com/corneliusweig/ketall) did not work for me and seems very slow/brittle

# Release

- tag new release `git tag <TAG>`
- push release `git push --tags`
- `wget https://github.com/grosser/kubectl-get-all/archive/refs/tags/<TAG>.zip`
- `sha256sum <TAG>.zip`
- update `krew.yaml` with new url, tag, and sha
- commit and push
- remove old: `kubectl krew remove get-all`
- test install new: `kubectl krew install --manifest-url https://raw.githubusercontent.com/grosser/kubectl-get-all/master/krew.yaml`

# TODO

- covert to go
- get into krew
