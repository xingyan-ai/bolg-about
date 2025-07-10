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

## 更新日志

### 2024-07-28: 关于页面重大更新与个性化

**1. "关于我"页面 - 盖洛普优势模块重构**
   - **数据更新**: 在 `source/_data/about.yml` 中完整录入了全部20项盖洛普优势才干，包含领域、名称、描述和对应颜色。
   - **动态展示**:
     - **旧方案问题**: 最初尝试通过JavaScript动态修改DOM内容，但因Hexo的Pjax刷新机制导致元素引用失效，出现内容无法同步更新的顽固bug。
     - **新方案解决**: 最终采用了一种更稳定、简单的方案。在 `about.pug` 模板中，一次性将20个才干的信息全部渲染成HTML，默认只显示第一个。然后通过一段独立的、无依赖的JavaScript脚本，定时切换显示/隐藏这些预渲染好的区块，并同步更新DNA动画颜色。此方案彻底解决了Pjax带来的问题。
     - **细节修复**: 修复了才干名称的文字颜色，使其与DNA动画中的高亮颜色保持一致。

**2. "关于我"页面 - 个性化设置**
   - **更换头像**: 在 `source/_data/about.yml` 中将 `avatarImg` 从网络链接修改为本地图片路径 `/img/touxiang.jpg`，提升加载速度和稳定性。
   - **移除网站图标 (Favicon)**: 在 `themes/anzhiyu/_config.yml` 中注释掉了 `favicon` 的配置，清除了浏览器标签页的图标。
   - **头像状态点**: 尝试将头像右下角的状态点颜色由绿色改为黑色，但未最终生效，此问题待后续排查。

**3. 分支与合并**
   - 所有开发工作在 `feature/gallup-strengths` 分支上进行。
   - 完成后，已成功将该分支合并到 `main` 主干。

### 2024-12-31: About 页面导航栏显示优化

**导航栏显示控制**
   - **需求**: 仅在 about 页面显示顶部导航栏，其他页面保持隐藏。
   - **技术方案**: 
     - **page.pug 修改**: 为 about 页面特殊处理，强制启用 `top_img` 属性，确保顶部区域渲染。
     - **主题配置调整**: 启用导航栏功能 (`nav.enable: true`)，使导航栏组件正常工作。
     - **header 条件优化**: 修改 `header/index.pug`，增加 about 页面的特殊渲染条件，即使在 `disable_top_img: true` 的情况下也能显示。
   - **实现效果**: about 页面显示导航栏，其他页面保持原有的隐藏状态，完美满足个性化需求。

**分支信息**
   - 开发分支: `about-navigation-modification`
   - 当前状态: 已完成开发和测试 

