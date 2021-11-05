# kubeadm编译100年

```shell
git reset --hard v1.22.3
mkdir .github/workflows/
curl -o .github/workflows/kubeadm.yml https://github.com/21ki/github-action/raw/main/kubeadm-build-99year/kubeadm.yml
git add .github/workflows/kubeadm.yml
git commit -am "kubeadm_build"
git tag  v1.22.3-patch-1.0 -f
git push origin v1.22.3-patch-1.0 -f
```
