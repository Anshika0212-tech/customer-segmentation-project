# Customer Segmentation Project

Segment customers by **behaviour** and **demographics** using K-Means clustering (Python / scikit-learn), with a Power BI dashboard guide.

## Files
| File | What it is |
|---|---|
| `Customer_Segmentation_Project.ipynb` | Main deliverable: full analysis, already executed with all outputs |
| `Customer_Segmentation_Report.html` | Same notebook as a single web page (open in any browser, no Python needed) |
| `customer_data_raw.csv` | Input data (raw, with real-world data-quality problems) |
| `customer_segments.csv` | Cleaned data + segment label + RFM scores (load this into Power BI) |
| `segment_summary.csv` | One-page profile of each segment |
| `segmentation_model.joblib` | Trained scaler + K-Means; use `assign_segment()` in the notebook to label new customers |
| `charts/` | All 20 charts as PNG, ready for slides or a report |

## How to run
```bash
pip install -r requirements.txt
jupyter notebook Customer_Segmentation_Project.ipynb   # Run > Run All Cells
```
Keep `customer_data_raw.csv` in the same folder as the notebook.

## Before you submit
1. Replace `[Your Name]`, `[Company Name]`, `[Mentor Name]` in the first cell and the last cell.
2. If your company gave you a real dataset, set `DATA_PATH` in Section 2 and make sure the column names match the data dictionary (or rename your columns). Then re-check Section 7 (number of clusters) and update the segment names/strategies in Section 11 to match your results.
3. State clearly in your submission that the included dataset is simulated.

## Questions you may be asked (and short answers)
- **Why K-Means?** Simple, fast, easy to explain to business teams. I validated it against Hierarchical and Gaussian Mixture clustering (ARI about 0.99) and a 30-run bootstrap (stability about 0.999).
- **Why K = 5?** Elbow suggests 5, silhouette is tied between 4 and 5 (0.323 vs 0.318), and the 5th cluster splits one group into two with very different income, order value and household size, so it adds business value.
- **Why scale the data?** K-Means uses distances; without scaling, income (tens of thousands) would dominate the other features.
- **Why is Monetary not in the model?** It equals Frequency x Avg_Order_Value, so including it would count spend twice. It is used for profiling instead.
- **Why not use category/channel in clustering?** K-Means uses Euclidean distance, which does not suit dummy variables. They are used to describe the segments (K-Prototypes is a possible next step).
- **What is RFM?** Recency (days since last purchase), Frequency (orders), Monetary (total spend): the classic customer-value framework.
- **What does the silhouette score of 0.32 mean?** Reasonable, clear structure with some natural overlap between segments (it ranges from -1 to 1).
