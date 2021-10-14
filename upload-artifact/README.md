# [upload-artifact](https://github.com/actions/upload-artifact)
```yml
    - name: Package
      run: mkdir myki && cp ./_output/local/bin/linux/amd64/kubeadm myki

    - uses: actions/upload-artifact@v1
      with:
        name: kubeadm-${{ env.packageName }}
        path: myki
```        
# [阳明大佬](https://github.com/cnych/go-github-actions/blob/v0.1.0/.github/workflows/release.yml)

# [木子李](https://blog.k8s.li/build-k8s-binary-by-github-actions.html)
# https://github.com/softprops/action-gh-release
```yml
      - name: Prepare for upload
        shell: bash
        run: |
          mv _output/dockerized/bin/linux/amd64/kubeadm kubeadm-linux-amd64
          mv _output/dockerized/bin/linux/arm64/kubeadm kubeadm-linux-arm64
          sha256sum kubeadm-linux-{amd64,arm64} > sha256sum.txt

      # 使用 softprops/action-gh-release 来将构建产物上传到 GitHub release 当中
      - name: Release and upload packages
        uses: softprops/action-gh-release@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          files: |
            sha256sum.txt
            kubeadm-linux-amd64
            kubeadm-linux-arm64
```            
