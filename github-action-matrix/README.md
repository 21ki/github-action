# 并发执行
# 示例
```shell
jobs:
  build:
    runs-on: ubuntu-latest #描述执行的操作系统
    strategy:
      matrix: #参数矩阵,每一个元素都会被带入步骤执行
        python-version: [3.6, 3.7, 3.8, 3.9]
```

# 示例2
```shell
on: push
jobs:
  node:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-16.04, ubuntu-18.04]
        node: [6, 8, 10]
    steps:
      - uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node }}
      - run: node --version
```
# 示例3
```shell
build:
    needs: [lint, test]
    strategy:
        matrix:
          os: [ubuntu-latest, macos-latest, windows-latest]
          node: ["12", "13", "14"]
    name: build - ${{ matrix.os }} - ${{ matrix.node }}
    runs-on: ${{ matrix.os }}
    steps:
      - uses: actions/checkout@v2
      - name: Use Node.js
        uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node }}
      - name: Load node_modules
        uses: actions/cache@v2
        with:
          path: |
            node_modules
            */*/node_modules
          key: ${{ runner.os }}-${{ hashFiles('**/package.json') }}
      - run: yarn build # 执行构建
      - name: Upload artifact # 上传构建产物，这里我们的源码目录是 src，而实际运行的代码是构建后的 bin 目录
        uses: actions/upload-artifact@v2
        with:
          name: build_output
          path: bin # 上传 bin 目录
```
