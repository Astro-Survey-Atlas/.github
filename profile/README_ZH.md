# Astro-Survey-Atlas

[English](./README.md) | **简体中文**

**Play With Your Own Astro Data.**

Astro-Survey-Atlas 是一套小而完整的开源工具：巡天覆盖、你自己的观测数据、以及 HEALPix/MOC。目标是看清某一片天区有什么，并且只取覆盖它的那些文件。

联系：[aaron@72602.space](mailto:aaron@72602.space)

---

## 我们在解决什么

### 1. 这片天区有哪些公开数据？
各巡天（CSST、SkyMapper、2MASS 等）的覆盖会重叠。我们用 HEALPix/MOC 给 footprint 建索引，让交叉覆盖一眼能看出来。

### 2. 你自己已经有哪些数据？
本地 FITS、星表、望远镜覆盖不该和公开巡天各管各的。Workspace 负责把它们叠在一起。

### 3. 怎样只拿需要的文件？
不要为了一小块天区去下整个巡天。先把天区落到 HEALPix 格子，再反查覆盖这些格子的具体文件。

---

## 项目

下面这些才是现在的公开仓库。没有 `sky-footprint-mapper`、`astro-atlas-core`、`astro-data-fetcher`、`cosmos-explorer-ui`。

| 项目 | 职责 | 技术栈 |
| --- | --- | --- |
| [**Assets**](https://github.com/Astro-Survey-Atlas/Assets) | 公开巡天目录、覆盖图、MOC、Resource Package v3。 | TypeScript |
| [**Workspace**](https://github.com/Astro-Survey-Atlas/Workspace) | 个人天文数据工作区：Aladin / MCP，用来叠你自己的数据。 | TypeScript |
| [**Warehouse**](https://github.com/Astro-Survey-Atlas/Warehouse) | Kubernetes Operator：扫描本地 / S3 / OSS 天文文件，抽出天区覆盖，发布 `CoverageLayer` 索引。不代理、不裁科学数据本身。 | Helm / Kubernetes |
| [**MOC-Core-SDK**](https://github.com/Astro-Survey-Atlas/MOC-Core-SDK) | 共享的离线 HEALPix/MOC 内核（`astro-survey-moc-core`）：ICRS/NESTED 像元、IVOA FITS MOC、Resource Package v3。Assets、Workspace、Warehouse 都用它。 | Python |

链路：**Assets**（公开目录）→ **Workspace**（你的数据）→ **Warehouse**（扫描 / 索引）→ **MOC-Core-SDK**（几何内核）。

---

## 参与

Issue 请开在对应仓库。Assets、Warehouse、MOC-Core-SDK 使用 Apache-2.0。

---

> "Somewhere, something incredible is waiting to be known." —— 卡尔·萨根
