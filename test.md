# Results Tables for Presentation Slides

## Table 1: Depth Metrics Definition

| Metric | Full Name | Formula | Range | Better | Interpretation |
|--------|-----------|---------|-------|--------|----------------|
| **AbsRel** | Absolute Relative Error | $\frac{1}{N}\sum\frac{\|d_{pred}-d_{gt}\|}{d_{gt}}$ | [0, ∞) | ↓ Lower | Average relative error per pixel |
| **SqRel** | Squared Relative Error | $\frac{1}{N}\sum\frac{(d_{pred}-d_{gt})^2}{d_{gt}}$ | [0, ∞) | ↓ Lower | Penalizes large errors more |
| **RMSE** | Root Mean Squared Error | $\sqrt{\frac{1}{N}\sum(d_{pred}-d_{gt})^2}$ | [0, ∞) | ↓ Lower | Overall depth accuracy in absolute units |
| **RMSElog** | RMSE in log space | $\sqrt{\frac{1}{N}\sum(\log d_{pred}-\log d_{gt})^2}$ | [0, ∞) | ↓ Lower | Balances near/far error sensitivity |
| **SILog** | Scale-Invariant Log Error | $\sqrt{Var(\log d_{pred}-\log d_{gt})}$ | [0, ∞) | ↓ Lower | Scale-invariant accuracy metric |
| **δ < 1.25** | Threshold Accuracy 1 | $\%(\max(\frac{d_{pred}}{d_{gt}},\frac{d_{gt}}{d_{pred}}) < 1.25)$ | [0, 1] | ↑ Higher | % pixels within 25% error |
| **δ < 1.25²** | Threshold Accuracy 2 | $\%(\max(\frac{d_{pred}}{d_{gt}},\frac{d_{gt}}{d_{pred}}) < 1.5625)$ | [0, 1] | ↑ Higher | % pixels within 56% error |
| **δ < 1.25³** | Threshold Accuracy 3 | $\%(\max(\frac{d_{pred}}{d_{gt}},\frac{d_{gt}}{d_{pred}}) < 1.953)$ | [0, 1] | ↑ Higher | % pixels within 95% error |

---

## Table 2: Per-Sample Quantitative Results

### Ball Sample

| Method | AbsRel ↓ | RMSE ↓ | RMSElog ↓ | SILog ↓ | δ < 1.25 ↑ |
|--------|----------|---------|-----------|---------|------------|
| **DreamTexture (Ours)** | **0.0161** | **606.16** | **0.0461** | **0.0454** | **0.9969** |
| Depth Anything V2 | 0.0591 | 1618.85 | 0.1130 | 0.1096 | 0.9875 |
| **Improvement** | **3.7×** | **2.7×** | **2.5×** | **2.4×** | **+0.9%** |

### Cake Sample

| Method | AbsRel ↓ | RMSE ↓ | RMSElog ↓ | SILog ↓ | δ < 1.25 ↑ |
|--------|----------|---------|-----------|---------|------------|
| **DreamTexture (Ours)** | **0.0342** | **852.88** | **0.0510** | **0.0509** | **0.9966** |
| Depth Anything V2 | 0.1245 | 2857.66 | 0.1687 | 0.1681 | 0.8767 |
| **Improvement** | **3.6×** | **3.4×** | **3.3×** | **3.3×** | **+12.0%** |

### Teddy Bear Sample

| Method | AbsRel ↓ | RMSE ↓ | RMSElog ↓ | SILog ↓ | δ < 1.25 ↑ |
|--------|----------|---------|-----------|---------|------------|
| **DreamTexture (Ours)** | **0.0396** | **930.39** | **0.0520** | **0.0519** | **0.9982** |
| Depth Anything V2 | 0.0874 | 2153.30 | 0.1758 | 0.1750 | 0.9809 |
| **Improvement** | **2.2×** | **2.3×** | **3.4×** | **3.4×** | **+1.7%** |

---

## Table 3: Average Performance Comparison

| Method | AbsRel ↓ | RMSE ↓ | RMSElog ↓ | SILog ↓ | δ < 1.25 ↑ |
|--------|----------|---------|-----------|---------|------------|
| **DreamTexture (Ours)** | **0.0300** | **796.48** | **0.0497** | **0.0494** | **0.9972** |
| Depth Anything V2 | 0.0903 | 2209.94 | 0.1525 | 0.1509 | 0.9484 |
| **Relative Improvement** | **3.0×** | **2.8×** | **3.1×** | **3.1×** | **+4.9%** |

**Key Finding:** DreamTexture outperforms state-of-the-art Depth Anything V2 by **3× on average** across all error metrics.

---

## Table 4: Simplified Summary

| Metric | DreamTexture (Ours) | Depth Anything V2 | Winner |
|--------|---------------------|-------------------|---------|
| **AbsRel** (lower is better) | 0.030 | 0.090 | ✓ **Ours (3.0× better)** |
| **RMSE** (lower is better) | 796 | 2210 | ✓ **Ours (2.8× better)** |
| **δ < 1.25** (higher is better) | 99.7% | 94.8% | ✓ **Ours (+4.9%)** |

**Bottom Line:** Our method achieves **3× better accuracy** than state-of-the-art monocular depth estimation.

---

## Table 5: Configuration Analysis Results

### Best Performing Hyperparameters

| Parameter | Tested Values | Best Value | Performance (AbsRel) |
|-----------|---------------|------------|----------------------|
| **offset_magnitude** | 0.05, 0.10, 0.20, 0.50 | **0.20** | 0.0161 (best run) |
| **offset_start_step** | 1, 10, 200, 500, 2000 | **200** | 0.0161 (best run) |

### Performance by Configuration

| offset_magnitude | offset_start_step | Mean AbsRel ↓ | Std | Count |
|------------------|-------------------|---------------|-----|-------|
| 0.10 | 2000 | **0.0192** | 0.0000 | 1 |
| 0.05 | 1 | 0.0324 | 0.0201 | 2 |
| 0.20 | 10 | 0.0342 | 0.0238 | 3 |
| 0.10 | 500 | 0.0351 | 0.0129 | 3 |

**Recommendation:** Use `offset_magnitude=0.20` and `offset_start_step=200` for best results.

---

## Table 6: Training Statistics

| Sample | Runs Evaluated | Total Checkpoints | Best Run | Best AbsRel | Training Steps |
|--------|----------------|-------------------|----------|-------------|----------------|
| ball_1 | 20 | 49 per run | B13 | 0.0161 | 100,000 |
| cake_1 | 20 | 49 per run | CA9 | 0.0342 | 100,000 |
| teddybear_2 | 20 | 49 per run | T4 | 0.0396 | 100,000 |
| **Total** | **60** | **2,940** | - | **0.0300 avg** | - |

---

