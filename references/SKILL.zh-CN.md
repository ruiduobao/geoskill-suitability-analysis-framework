# 适宜性分析框架 | Suitability Analysis Framework

多准则适宜性分析流水线：因子标准化（min-max 正/负向、模糊隶属度）→ 权重确定（AHP 特征向量法 + 一致性检验 CR，或熵权法客观赋权）→ 加权线性叠加 → 适宜性分级（等间距/分位数）。

## 核心算法

- 因子标准化 + 模糊隶属度
- AHP（一致性检验）/ 熵权法
- 加权叠加 + 适宜性分级

## 依赖

```bash
pip install numpy rasterio scipy
```

## 使用方法

### 示例 1（合成数据，离线）

```bash
python geoskill-suitability-analysis-framework.py --bbox 116.0 39.0 117.0 40.0 --synthetic --output-dir ./out
```

### 示例 2（指定区域 + 静默）

```bash
python geoskill-suitability-analysis-framework.py --bbox 121.0 31.0 122.0 32.0 --synthetic --output-dir ./out2 --quiet
```

### 示例 3（真实输入）

```bash
python geoskill-suitability-analysis-framework.py --input <你的数据文件> --output-dir ./out3
```

### 示例 4（极小区域边界测试）

```bash
python geoskill-suitability-analysis-framework.py --bbox 116.39 39.90 116.40 39.91 --synthetic --output-dir ./out4 --quiet
```

## 输出

| 文件 | 格式 | 说明 |
|---|---|---|
| `suitability_score.tif` | GeoTIFF/GeoJSON/JSON | 主产物 |
| `suitability_class.tif` | GeoTIFF/GeoJSON/JSON | 主产物 |
| `suitability_stats.json` | GeoTIFF/GeoJSON/JSON | 主产物 |
| `output-manifest.json` | JSON | 运行清单 |

## 数据源 / Source

- 合成模式：本地生成物理一致的模拟数据，无外部数据源。
- 真实模式：读取本地输入文件，无网络请求。

## 隐私声明 / Privacy

- 默认完全离线运行，不发起任何网络请求。
- `--synthetic` 模式不读取任何外部数据。
- 所有计算在本地完成，不上传用户数据。

## License

MIT
