<p align="center">
  <img src="../static/asa-logo-long-rotate.svg" alt="Astro-Survey-Atlas Logo" width="100%" max-width="1000px">
</p>

# Astro-Survey-Atlas 🌌🔭

[English](./README.md) | **简体中文**

**Play With Your Own Astro Data.**

Astro-Survey-Atlas 是一套致力于构建下一代、高性能且极具视觉冲击力的开源天文工具集。我们专注于天文巡天覆盖范围（Footprints）、用户私有观测数据以及 HEALPix/MOC 空间索引。
我们的使命是消除复杂天文观测数据与直观、研究级可视化之间的壁垒，让天文学家、科研人员和天文爱好者能够一目了然地看清某一片天区存在哪些数据，并精准获取覆盖该区域的具体文件。

联系方式：[aaron@72602.space](mailto:aaron@72602.space)

---

## 🎯 我们解决的核心问题

在现代观测天文学中，研究人员和天文爱好者常常被来自各大天区巡天计划的浩瀚数据所淹没。我们构建的工具旨在直接解决天文数据工作流中的三个根本问题：

### 1. 🔍 这片天区有哪些公开数据？（公开数据检索与发现）
伴随着无数天文台和卫星项目（如 SDSS, Gaia, JWST, Euclid, DESI, Pan-STARRS, CSST 等）释放出 PB 级别的星空图像和星表，要找出在目标坐标处到底存在哪些观测数据，往往是一项极其繁琐的工程。
* **我们的解决方案：** 我们系统性地扫描并整合各大公开巡天项目的覆盖范围（Footprints），通过空间分级索引（如 HEALPix/MOC）快速筛选出不同巡天在天球上重合覆盖的区域，让用户一目了然地知道在哪些天区存在可供交叉研究的多波段数据。

### 2. 📂 你自己已经有哪些数据？（用户私有数据的管理与融合）
天文学家经常需要处理自己本地的星表、原始的 FITS 图像或特定望远镜的观测范围，但往往缺乏一种简单且现代的方式来对这些私有数据进行编目并与公开巡天叠加可视化。
* **我们的解决方案：** 我们提供轻量化的个人工作区与核心 SDK，用于为你自己的数据集生成空间覆盖范围和本地索引，使你能够无缝地将私有观测数据与公开巡天图像叠加在一起进行对比和可视化。

### 3. ⚡ 怎样只拿需要的文件？（按需精准检索与关联文件解析）
仅为了分析一小片天区而下载整个数 TB 甚至数 PB 级别的完整星表或图像库，是极其低效且浪费资源的。
* **我们的解决方案：** 针对重合的天区范围，我们先粗筛出重合覆盖的 HEALPix 区域，再由这些 HEALPix 索引反推出在此空间范围内所涉及的具体数据文件（如 FITS 文件或星表切片）。通过这种“天区范围 -> 重合 HEALPix -> 具体关联文件”的映射机制，用户只需下载极少数的目标文件，从而大幅度降低数据下载的体量与难度。

---

## 🚀 核心生态与项目

以下是我们针对解决这三大核心痛点而开发的真实公开项目矩阵：

| 项目名称 (Project) | 职责 & 解决核心问题 | 技术栈 (Tech Stack) | 当前状态 |
| :--- | :--- | :--- | :--- |
| [**Assets**](https://github.com/Astro-Survey-Atlas/Assets) | **1. 公开数据发现**<br>公开巡天目录、覆盖图、MOC、Resource Package v3。 | TypeScript | 🗺️ 活跃开发 |
| [**Workspace**](https://github.com/Astro-Survey-Atlas/Workspace) | **2. 个人数据融合**<br>个人天文数据工作区：基于 Aladin / MCP 叠层展示本地和用户私有数据。 | TypeScript | 🏗️ 活跃开发 |
| [**Warehouse**](https://github.com/Astro-Survey-Atlas/Warehouse) | **3. 按需精准获取**<br>Kubernetes Operator：扫描本地、S3 和 OSS 天文文件，抽出天区覆盖，发布 `CoverageLayer` 索引，不代理/裁剪科学数据。 | Helm / Kubernetes | ⚡ 活跃开发 |
| [**MOC-Core-SDK**](https://github.com/Astro-Survey-Atlas/MOC-Core-SDK) | **2 & 3. 几何核心内核**<br>共享的离线 HEALPix/MOC 内核（`astro-survey-moc-core`）：ICRS/NESTED 像元、IVOA FITS MOC、Resource Package v3。 | Python | 🔧 活跃开发 |

### 🔄 系统数据流向
```
Assets (公开数据目录) ──> Workspace (个人工作区 & 叠层可视化)
                                │
                                ▼
MOC-Core-SDK (几何内核) <── Warehouse (S3/OSS 存储扫描与索引器)
```

---

## 🤝 欢迎加入与贡献！

我们坚信，星空属于每一个人，开源科学也是如此！无论你是专业的天体物理学者、软件工程师、前端/UI设计师，还是对宇宙充满好奇的业余天文爱好者，这里都有属于你的位置。

### 你可以如何参与贡献：
1. **💻 代码与设计：** 参与核心仓库开发，优化空间查询性能，或为星图设计更优美的视觉呈现。
2. **📝 文档与翻译：** 协助编写使用手册、科普教程，或帮助我们将专业天文术语本地化。
3. **🧪 科学与数据：** 为我们推荐或提供新的巡天覆盖区域数据、天体星表或科研用例。
4. **💬 反馈与创意：** 开启讨论（Discussions）、提交 Bug 报告，或与大家分享你的天文探索项目。

Issue 请提交在受影响的具体仓库。本组织下的 Assets、Warehouse 和 MOC-Core-SDK 项目采用 Apache-2.0 开源协议。

---

## 💬 建立联系

加入我们的社区，获取最新动态，提问或分享你的绝妙创意！

* **GitHub Discussions：** 在我们的 [讨论区](https://github.com/orgs/Astro-Survey-Atlas/discussions) 畅所欲言！
* **反馈与建议：** 遇到问题或有功能需求？请在相关项目的 Repository 下直接提交 Issue。

---

> "Somewhere, something incredible is waiting to be known." —— 卡尔·萨根 (Carl Sagan)
