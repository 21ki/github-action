# 同步fork仓库防止删库
git checkout -b myki
rm -rf *
mkdir .github/workflows/ -p
curl -o https://ghproxy.com/https://raw.githubusercontent.com/21ki/github-action/main/github-fork-sync/repo-sync.yml .github/workflows/repo-sync.yml
git add .
git commit -m "README"
git push --set-upstream origin myki
