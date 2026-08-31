# Astro-Survey-Atlas

**English** | [简体中文](./README_ZH.md)

**Play With Your Own Astro Data.**

Astro-Survey-Atlas is a small open-source stack for survey footprints, your own observations, and HEALPix/MOC coverage — so you can see what exists on a patch of sky and fetch only the files that cover it.

Contact: [aaron@72602.space](mailto:aaron@72602.space)

---

## What we solve

### 1. What public data is on this patch of sky?
Public surveys (CSST, SkyMapper, 2MASS, and others) publish overlapping imaging and catalogs. We index their footprints with HEALPix/MOC so you can see where they intersect.

### 2. What data do you already have?
Your own FITS, catalogs, and observatory footprints should sit next to the public sky, not in a separate pile. Workspace is that overlay.

### 3. How do you get only the files you need?
Instead of downloading whole surveys, we map a sky region to HEALPix cells and then to the concrete files that cover those cells.

---

## Projects

These are the public repositories. There is no `sky-footprint-mapper`, `astro-atlas-core`, `astro-data-fetcher`, or `cosmos-explorer-ui`.

| Project | Role | Stack |
| --- | --- | --- |
| [**Assets**](https://github.com/Astro-Survey-Atlas/Assets) | Public survey directory, coverage maps, MOCs, and Resource Package v3. | TypeScript |
| [**Workspace**](https://github.com/Astro-Survey-Atlas/Workspace) | Your personal astro data workspace — Aladin / MCP plane for local and user data. | TypeScript |
| [**Warehouse**](https://github.com/Astro-Survey-Atlas/Warehouse) | Kubernetes operator that scans local, S3, and OSS astronomy files, extracts sky coverage, and publishes `CoverageLayer` indices. It does not proxy or reduce scientific payloads. | Helm / Kubernetes |
| [**MOC-Core-SDK**](https://github.com/Astro-Survey-Atlas/MOC-Core-SDK) | Shared offline HEALPix/MOC kernel (`astro-survey-moc-core`): ICRS/NESTED cells, IVOA FITS MOCs, Resource Package v3. Used by Assets, Workspace, and Warehouse. | Python |

Flow: **Assets** (public catalog) → **Workspace** (your data) → **Warehouse** (scan / index) → **MOC-Core-SDK** (geometry).

---

## Contribute

Issues belong on the repository they affect. This organization is Apache-2.0 on Assets, Warehouse, and MOC-Core-SDK.

---

> "Somewhere, something incredible is waiting to be known." — Carl Sagan
