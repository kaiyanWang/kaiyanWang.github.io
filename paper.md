---
layout: article  # 改用article布局（和About一致，支持更多Theme特性）
titles:
  en: Paper
  zh-Hans: 项目展示
key: page-paper  # 让Theme自动映射URL为/project.html（无需写permalink）
article_header:
  type: cover
  image:
    src: /assets/images/blogs/project-header.jpg  # 顶部封面图
    alt: 项目展示封面
---

## 我的项目集

这里展示我开发或参与的项目，包含详细介绍、技术栈和演示链接：

<!-- 项目卡片1：用HTML+CSS实现卡片式布局（TeXt Theme支持内嵌CSS） -->
<div style="display: flex; gap: 20px; margin: 30px 0; flex-wrap: wrap;">
  <div style="flex: 1; min-width: 300px; border: 1px solid #eee; padding: 20px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1);">
    <h3 style="margin-top: 0;">XXX个人博客系统</h3>
    <img src="/assets/images/blogs/project1.png" alt="博客系统截图" style="width: 100%; border-radius: 4px; margin: 10px 0;">
    <p><strong>技术栈：</strong>Jekyll + TeXt Theme + GitHub Actions</p>
    <p><strong>功能：</strong>自动部署、响应式布局、标签分类、多语言支持</p>
    <p>
      <a href="https://你的用户名.github.io" target="_blank" style="color: #42b983;">在线演示</a> | 
      <a href="https://github.com/你的用户名/仓库名" target="_blank" style="color: #42b983;">GitHub仓库</a>
    </p>
  </div>

  <div style="flex: 1; min-width: 300px; border: 1px solid #eee; padding: 20px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1);">
    <h3 style="margin-top: 0;">Vue管理系统</h3>
    <img src="/assets/images/blogs/project2.png" alt="管理系统截图" style="width: 100%; border-radius: 4px; margin: 10px 0;">
    <p><strong>技术栈：</strong>Vue 3 + Vite + Element Plus + Pinia</p>
    <p><strong>功能：</strong>权限控制、数据可视化、表单校验、Excel导出</p>
    <p>
      <a href="https://demo.你的项目地址.com" target="_blank" style="color: #42b983;">在线演示</a> | 
      <a href="https://github.com/你的用户名/仓库名2" target="_blank" style="color: #42b983;">GitHub仓库</a>
    </p>
  </div>
</div>

<!-- 项目卡片2：用Theme内置的提示框/标签增强可读性 -->
### 开源工具：Markdown编辑器
> **技术栈**：React + TypeScript + Monaco Editor  
> **简介**：轻量级Markdown编辑器，支持实时预览、代码高亮、图片拖拽上传  
> **状态**：持续开发中  
> <a href="https://github.com/你的用户名/md-editor" target="_blank">GitHub →</a>

<!-- 图片画廊：多图展示项目细节 -->
### 项目细节展示
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 10px; margin: 20px 0;">
  <img src="/assets/images/blogs/detail1.png" alt="细节1" style="width: 100%; border-radius: 4px;">
  <img src="/assets/images/blogs/detail2.png" alt="细节2" style="width: 100%; border-radius: 4px;">
  <img src="/assets/images/blogs/detail3.png" alt="细节3" style="width: 100%; border-radius: 4px;">
</div>