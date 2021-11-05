# kubeadm编译100年

```shell
git reset --hard v1.22.3
mkdir .github/workflows/
vi .github/workflows/kubeadm.yml
git add .github/workflows/kubeadm.yml
git commit -am "kubeadm_build"
git tag  v1.22.3-patch-1.0 -f
git push origin   v1.22.3-patch-1.0 -f
```
