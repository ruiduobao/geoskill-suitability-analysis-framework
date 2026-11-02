---
name: geoskill-suitability-analysis-framework
description: '因子标准化+AHP/熵权法赋权+加权叠加+适宜性分级'
---

# 适宜性分析框架 | Suitability Analysis Framework

Multi-criteria suitability analysis pipeline: factor standardization (min-max positive/negative directions, fuzzy membership) → weight determination (AHP eigenvector method + consistency check CR, or objective entropy weight method) → weighted linear combination → suitability classification (equal interval / quantile).

## Core Algorithm / 核心算法

- Factor standardization + fuzzy membership
- AHP (consistency check) / entropy weight method
- Weighted overlay + suitability classification

## Dependencies / 依赖

```bash
pip install numpy rasterio scipy
```

## Usage / 使用方法

### Example 1 (synthetic data, offline)

```bash
python geoskill-suitability-analysis-framework.py --bbox 116.0 39.0 117.0 40.0 --synthetic --output-dir ./out
```

### Example 2 (custom region + quiet mode)

```bash
python geoskill-suitability-analysis-framework.py --bbox 121.0 31.0 122.0 32.0 --synthetic --output-dir ./out2 --quiet
```

### Example 3 (real input)

```bash
python geoskill-suitability-analysis-framework.py --input <your data file> --output-dir ./out3
```

### Example 4 (tiny-area boundary test)

```bash
python geoskill-suitability-analysis-framework.py --bbox 116.39 39.90 116.40 39.91 --synthetic --output-dir ./out4 --quiet
```

## Output / 输出

| File | Format | Description |
|---|---|---|
| `suitability_score.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `suitability_class.tif` | GeoTIFF/GeoJSON/JSON | Primary output |
| `suitability_stats.json` | GeoTIFF/GeoJSON/JSON | Primary output |
| `output-manifest.json` | JSON | Run manifest |

## Data Source / 数据源 / Source

- Synthetic mode: locally generates physically consistent simulated data; no external data sources.
- Real-data mode: reads local input files; no network requests.

## Privacy / 隐私声明 / Privacy

- Runs fully offline by default; makes no network requests.
- `--synthetic` mode reads no external data.
- All computation is done locally; user data is never uploaded.

## License / License

MIT

---

> 中文完整版：需要时再读 [references/SKILL.zh-CN.md](references/SKILL.zh-CN.md)，不要默认全量加载。
