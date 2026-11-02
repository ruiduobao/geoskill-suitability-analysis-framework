# Suitability Analysis Framework (geoskill-suitability-analysis-framework)

> Factor standardization + AHP/entropy-weight weighting + weighted overlay + suitability classification

---

## 1. Overview

Multi-criteria suitability analysis pipeline: factor standardization (min-max for positive/negative directions, fuzzy membership) → weight determination (AHP eigenvector method + consistency check CR, or objective weighting with the entropy weight method) → weighted linear overlay → suitability classification (equal interval / quantile).

## 3. Quick Start

```bash
pip install -r requirements.txt
python geoskill-suitability-analysis-framework.py --bbox 116 39 117 40 --synthetic --output-dir ./out
```

## 4. CLI Parameters

Run `python <skill>.py --help` for the full list. Common parameters:

| Parameter | Type | Description |
|---|---|---|
| `--bbox` | `float[4]` | WGS84 bounding box `min_lon min_lat max_lon max_lat` |
| `--input` | `path` | Local input file (GeoJSON/GeoTIFF/etc.) |
| `--output-dir` | `path` | Output directory (default `./output`) |
| `--synthetic` | `flag` | Use synthetic data instead of real input |
| `--quiet` | `flag` | Suppress non-essential stdout |

## 5. Input / Output

| File | Format | Description |
|---|---|---|
| `suitability_score.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `suitability_class.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `suitability_stats.json` | GeoTIFF/GeoJSON/JSON | Primary output |
| `output-manifest.json` | JSON | Run manifest |

## 6. Technical Principle

- Factor standardization + fuzzy membership
- AHP (consistency check) / entropy weight method
- Weighted overlay + suitability classification

## 8. License

MIT License. See [`LICENSE`](./LICENSE) for full text.

---

> 中文完整版：[references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)
