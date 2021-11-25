# https://nebula-graph.com.cn/posts/automate-workflows-with-github-action/
    - name: Cleanup
        if: always()
        run: rm -rf build
将 step 的运行条件设置为 always() 确保每次任务都要执行该步骤，即便中途出错。

