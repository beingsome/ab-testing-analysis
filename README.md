# A/B测试：营销广告对用户转化率的效果评估

**项目类型**：独立完成的A/B测试分析项目  
**数据来源**：Kaggle Marketing A/B Testing Dataset  
**数据量**：588,101 条用户记录  
**技术栈**：Python (Pandas, Scipy, Statsmodels, Scikit-learn)

---

## 🔍 核心发现

- **主效应**：商业广告显著提升转化率，绝对提升 0.77 个百分点（相对提升 43%），Z=7.37，P<0.001。
- **Bootstrap稳健性检验**：95% 置信区间 [0.59%, 0.94%]，不包含 0，结论稳健。
- **时间异质性**：广告效果因星期几而异（周一、二、三、六显著，周四、周日无效），交互效应显著（P=0.045）。
- **黄金时段**：下午 14:00-17:00 转化率超 3%，为最佳投放窗口；凌晨 1:00-3:00 效果最差（<1%）。

---

## 📁 项目文件

- `ab_test_report.ipynb` — 完整可运行的 Jupyter Notebook 分析报告
- `ab_test_report.pdf` — 导出的面试展示版报告

---

## 🔧 如何运行

在 Jupyter Notebook 中打开 `.ipynb` 文件即可运行。

依赖库：
- pandas, numpy, matplotlib
- scipy, statsmodels
- scikit-learn
