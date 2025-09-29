# XAI Assignment 4

**Name:** Tiffany Degbotse  
**Dataset:** Asaniczka. (2024). *Full TMDB Movies Dataset 2024 (1M Movies)* [Data set]. Kaggle. ODC Attribution License. Available at: https://www.kaggle.com/datasets/asaniczka/tmdb-movies-dataset-2023-930k-movies  

## Project Overview  
This project applies explainable AI (XAI) techniques to predict movie ratings using the TMDB dataset. The target variable is `vote_average`; the features are `budget`, `popularity`, `runtime`, and `vote_count`. The trained model is a Random Forest Regressor. Interpretability includes Partial Dependence (PDP), Individual Conditional Expectation (ICE) and Accumulated Local Effects (ALE)

## Installation  
```bash
pip install numpy==1.25.2 pandas==2.0.3 scikit-learn==1.2.2 shap==0.45.1
pip install git+https://github.com/MaximeJumelle/ALEPython.git@dev#egg=alepython
pip install scipy==1.13.1 seaborn==0.12.2 matplotlib==3.7.2
```  

## How to Run  
1. Place the dataset CSV in the `src/` folder of this repo.  
```
XAI_assignment4/
├── src/
│   └── TMDB_movie_dataset_v11.csv
└── global_explanations.ipynb
```
2. Open the notebook:  
   - Google Colab: Open from GitHub or upload the notebook.   
3. Run the cells in order:  
   - Load and clean data (drop NAs in `budget`, `popularity`, `runtime`, `vote_count`, `vote_average`; sample 5,000 rows).  
   - Train `RandomForestRegressor`.  
   - Generate interpretability outputs (PDP, ICE, ALE, correlation matrix).  
4. Expected outputs:  
   - PDP plots showing budget’s negative relationship with predicted ratings  
   - ICE plots highlighting heterogeneity in predictions  
   - ALE plots confirming trends across ranges  
   - Correlation matrix showing budget and vote_count correlation  

## Results Summary  
- Budget vs Ratings: predicted ratings decrease as budget increases, then plateau at very high budgets.  
- Correlation: the strongest pair is `budget`–`vote_count` (~0.60) with weaker relationships among other pairs.  
- ICE and ALE confirm heterogeneous effects across movies and reinforce the global PDP trend.  
- Interaction insight: popularity mitigates or can reverse budget’s negative effect on predicted ratings.  

## References  

**Dataset**  
Asaniczka. (2024). *Full TMDB Movies Dataset 2024 (1M Movies)* [Data set]. Kaggle. ODC Attribution License. Available at: https://www.kaggle.com/datasets/asaniczka/tmdb-movies-dataset-2023-930k-movies  

**Model**  
Breiman, L. (2001). Random forests. *Machine Learning, 45*(1), 5–32. https://doi.org/10.1023/A:1010933404324  

The above ReadMe  was generated using ChatGPT on 09/29/25 at 4:00am.
