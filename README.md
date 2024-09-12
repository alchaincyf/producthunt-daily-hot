# Product Hunt 每日中文热榜

[English](README.en.md) | [中文](README.md)

![License](https://img.shields.io/github/license/ViggoZ/producthunt-daily-hot) ![Python](https://img.shields.io/badge/python-3.x-blue)

Product Hunt 每日热榜是一个基于 GitHub Action 的自动化工具，它能够每天定时生成 Product Hunt 上的热门产品榜单 Markdown 文件，并自动提交到 GitHub 仓库中。该项目旨在帮助用户快速查看每日的 Product Hunt 热门榜单，并提供更详细的产品信息。

榜单会在每天下午4点自动更新，可以在 [🌐 这里查看](https://decohack.com/category/producthunt/)。

## 预览

![Preview](./preview.gif)

## 功能概述

- **自动获取数据**：每天自动获取前一天的 Product Hunt Top 30 产品数据。
- **关键词生成**：生成简洁易懂的中文关键词，帮助用户更好地理解产品内容。
- **高质量翻译**：使用 OpenAI 的 GPT-4 模型对产品描述进行高质量翻译。
- **Markdown 文件生成**：生成包含产品数据、关键词和翻译描述的 Markdown 文件。
- **每日自动化**：通过 GitHub Actions 自动生成并提交每日的 Markdown 文件。
- **自动部署到 Vercel**：生成的内容会自动部署到 Vercel，实现快速的静态网站更新。

## 快速开始

### 前置条件

- Python 3.x
- GitHub 账户及仓库
- OpenAI API Key
- Product Hunt API 凭证
- Vercel 账户及项目设置

### 设置

1. **GitHub Secrets：**

   在您的 GitHub 仓库中添加以下 Secrets：

   - `OPENAI_API_KEY`: 您的 OpenAI API 密钥。
   - `PRODUCTHUNT_CLIENT_ID`: 您的 Product Hunt API 客户端 ID。
   - `PRODUCTHUNT_CLIENT_SECRET`: 您的 Product Hunt API 客户端密钥。
   - `PAT`: 用于推送更改到仓库的个人访问令牌。
   - `VERCEL_TOKEN`: 您的 Vercel 部署令牌。
   - `VERCEL_ORG_ID`: 您的 Vercel 组织 ID。
   - `VERCEL_PROJECT_ID`: 您的 Vercel 项目 ID。

2. **Vercel 项目设置：**

   - 在 Vercel 上创建一个新项目，并将其连接到您的 GitHub 仓库。
   - 配置项目以使用生成的 Markdown 文件作为内容源。
   - 记录下项目的组织 ID 和项目 ID，并添加到 GitHub Secrets 中。

3. **GitHub Actions 工作流：**

   工作流定义在 `.github/workflows/generate_markdown.yml` 和 `.github/workflows/deploy_to_vercel.yml` 中。这些工作流会自动运行，生成内容并部署到 Vercel。

### 使用

设置完成后，GitHub Action 将自动生成并提交包含 Product Hunt 每日热门产品的 Markdown 文件，并自动部署到 Vercel。文件存储在 `data/` 目录下。

### 自定义

- 您可以修改 `scripts/product_hunt_list_to_md.py` 文件来自定义生成文件的格式或添加额外内容。
- 如果需要，可以在 `.github/workflows/generate_markdown.yml` 中调整定时任务的运行时间。

### 示例输出

生成的文件存储在 `data/` 目录下。每个文件以 `PH-daily-YYYY-MM-DD.md` 的格式命名。

### 贡献

欢迎任何形式的贡献！如有任何改进或新功能的建议，请提交 issue 或 pull request。

### 许可证

本项目基于 MIT 许可证开源 - 有关详细信息，请参阅 [LICENSE](LICENSE) 文件。
