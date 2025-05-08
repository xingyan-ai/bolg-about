# 我的个人博客 (bolg-about)

这是一个使用 [Hexo](https://hexo.io/) 博客框架和 [Anzhiyu](https://github.com/anzhiyu-c/hexo-theme-anzhiyu) 主题搭建的个人博客项目。

## 运行

1.  **安装依赖:**
    ```bash
    npm install
    ```

2.  **清理旧文件 (可选):**
    ```bash
    npx hexo clean
    ```

3.  **生成静态文件:**
    ```bash
    npx hexo generate
    ```

4.  **启动本地服务器:**
    ```bash
    npx hexo server
    ```
    默认访问地址: http://localhost:4000/

## 主要配置文件

*   `_config.yml`: Hexo 站点主配置文件。
*   `themes/anzhiyu/_config.yml`: Anzhiyu 主题配置文件。
*   `source/_data/about.yml`: "关于我" 页面的数据文件。
*   `source/_data/creativity.yml`: "关于我" 页面技能图标的数据文件。

## 版本

当前版本: v1.1 