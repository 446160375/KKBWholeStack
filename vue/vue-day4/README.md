# 看源码流程
* 调试环境搭建 
  * 安装依赖： npm i
  * 安装rollup： npm i -g rollup
  * 修改dev脚本，添加sourcemap，package.json
    ```
    "dev": "rollup -w -c scripts/config.js --sourcemap --environment TARGET:web-full-dev"
    ```
  * 运⾏开发命令： npm run dev
  * 引⼊前⾯创建的vue.js，samples/commits/index.html
    ```
      <script src="../../dist/vue.js"></script>
    ```
    ```
      术语解释：
      runtime：仅包含运⾏时，不包含编译器
      common：cjs规范，⽤于webpack1
      esm：ES模块，⽤于webpack2+
      umd: universal module definition，兼容cjs和amd，⽤于浏览器
    ```

### 注意
克隆项目后需要重新 npm run dev 下 要不然没有sourcemap

测试的用例在 examples -> test 文件下