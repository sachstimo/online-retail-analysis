# Online Retail Customer Segmentation Analysis

## Overview
This project analyzes an online retail dataset to segment customers based on purchasing behaviors. The goal is to optimize marketing and customer retention strategies by moving away from one-size-fits-all campaigns toward targeted approaches that maximize customer lifetime value.

## Project Structure
```
.
├── DATA/
│   └── Online Retail.xlsx       # Raw transaction data
├── INSTRUCTIONS/
│   └── BusinessCase - Unsupervised Clustering.pdf
├── PRESENTATION/
│   └── AI2_Clustering_Presentation_Timo Sachs.pdf
├── retail_analysis.ipynb        # Main analysis notebook
└── requirements.txt             # Python dependencies
```

## Dataset Description
The dataset contains transactions from a UK-based online retailer, covering the period from December 2010 to December 2011. Each record includes:

| Column       | Description                                                                        |
|--------------|------------------------------------------------------------------------------------|
| InvoiceNo    | Invoice number, 6-digit integral number uniquely assigned to each transaction      |
| StockCode    | Product code, 5-digit integral number uniquely assigned to each distinct product   |
| Description  | Product name                                                                       |
| Quantity     | The quantities of each product per transaction                                     |
| InvoiceDate  | Invoice date and time, day and time when transaction was generated                 |
| UnitPrice    | Unit price, product price per unit                                                 |
| CustomerID   | Customer number, 5-digit integral number uniquely assigned to each customer        |
| Country      | Country name, the name of the country where each customer resides                  |

## Analysis Process

### 1. Data Preprocessing
- Handled missing values in CustomerID and Description fields
- Removed returns (negative quantities) and rows with negative/zero prices
- Created additional features like TotalAmount for each transaction
- Eliminated problematic transactions (bank charges, etc.)

### 2. Feature Engineering
- **RFM Analysis**: Recency, Frequency, Monetary value
- **Purchase Patterns**: Average basket size, average basket value
- **Product Exploration**: Number of distinct items purchased
- **Temporal Metrics**: Purchase consistency, purchase coverage 
- **Geographic Segmentation**: UK vs. international customers

### 3. Clustering Approach
Three clustering algorithms were compared:
- K-means clustering
- Hierarchical clustering
- DBSCAN

Various preprocessing techniques were applied:
- Log transformation of skewed features
- Robust scaling to handle outliers
- Feature reduction and selection

### 4. Results
The analysis identified four distinct customer segments:

1. **Dormant Majority (68%)**: Inactive one-time buyers
   - 121 days since last purchase
   - Only 1.8 purchases on average
   - $661 total spend per customer
   - Limited product exploration (37 items)

2. **Occasional Spenders (24%)**: Moderate engagement
   - More recent activity (40 days)
   - Moderate frequency (5.8 purchases)
   - $2,257 lifetime value
   - Good product exploration (93 items)

3. **VIP Customers (8%)**: High-value loyalists
   - Very recent activity (13 days)
   - High frequency (20.3 purchases)
   - $12,058 lifetime value
   - Extensive product exploration (176 items)

4. **High-Volume Anomalies (<1%)**: Potential B2B accounts
   - Extremely high purchase volumes 
   - Likely wholesale or business customers

## Business Recommendations
1. **Personalized Marketing**: Create segment-specific campaigns
2. **Reactivation Strategy**: Win-back campaigns for dormant customers
3. **Loyalty Program**: Develop tiered benefits focusing on VIP retention
4. **Conversion Path**: Create clear pathways for occasional customers to become VIPs
5. **Product Recommendations**: Use segment-specific purchase patterns for personalization 
6. **Customer Retention**: Focus on keeping high-value customers engaged

## Technical Requirements
```
pandas>=1.3.0
numpy>=1.20.0  
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=0.24.0
scipy>=1.7.0
yellowbrick>=1.3.0
```

## Usage
Run the Jupyter notebook `retail_analysis.ipynb` to reproduce the analysis and visualize the customer segments.

```
jupyter notebook retail_analysis.ipynb
```