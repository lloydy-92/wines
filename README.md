# **IMPORTANT NOTE** #
The dataset used in this project, `winemag-data_first150k.csv`, is so large in fact that GitHub will not let me upload it as a file to this repository. If you wish to access the dataset yourself, please follow this link to download the project starter pack, courtesy of zackthoutt on Kaggle: (*https://www.kaggle.com/datasets/zynicide/wine-reviews*)



# Causal Inference Analysis - Wines: Overview and Objective
This project investigates potential causal relationships between wine characteristics — including geographic origin, wine type, price, and rating — using statistical and causal inference methods. Through a combination of ANOVA, Tukey’s post-hoc tests, and causal inference models, the project aims to reveal whether observed differences in ratings and prices are statistically or causally linked to wine characteristics.


## Key insights (Summary)
> For full results, visualisations, and detailed discussion, open the Jupyter notebook wines.ipynb in this repository.
- Cleaned messy columns, and dropped unneccessary and created useful columns, using ```pandas```.
- Visualised association between numeric (price and rating) and categorical (origin and type) variables using boxplots```matplotlib``` and ```seaborn```.
- Statistically tested for signifcant association between the variables by checking for data skewness, testing ANOVA assumptions, and choosing the correct test accordingly (`ANOVA`, `Welch ANOVA`, `Kruskal-Wallis`).
- Statistically tested for a causal link between numeric and categorical variables via the following:
  - **Propensity Score Matching (PSM)**: Matches similar observations to estimate causal effects of categorical treatments.
  - **Logistic Regression**: Models probability of treatment assignment.
  - **Nearest Neighbor Matching**: Matches wines with similar covariate distributions.
- Exported statistically testing results into separate `.csv` file `causal_inference_summary_auto_conf.csv` for easy comparison.
  
## Tools and Libraries
| Purpose | Libraries Used |
|----------|----------------|
| Data manipulation | `pandas`, `numpy` |
| Statistical testing | `scipy.stats`, `statsmodels`, `pingouin`, `scikit_posthocs` |
| Machine learning / Causal inference | `scikit-learn` |
| Data visualization | `matplotlib`, `seaborn` |
| Encoding & preprocessing | `LabelEncoder` |
| Environment | Jupyter Notebook (`%matplotlib inline`) |

## Installation
1. **Clone this repository**
   ```bash
   git clone https://github.com/lloydy-92/wines.git
   cd wines
2. **(Optional) Create and activate a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate       # On Windows use: venv\Scripts\activate
3. **Install dependencies**
   ```bash
   pip install pandas matplotlib seaborn sklearn scipy pingouin scikit_posthocs jupyter
4. **Launch the notebook**
   ```bash
   jupyter notebook wines.ipynb

## Project Structure
```bash
OKCupid/
├── wines.ipynb        # Main analysis notebook
├── causal_inference_summary_auto_conf.csv    # Exported table/.csv file of causal inference statistical analysis results
├── requirements.txt          # Python dependencies
└── README.md                 # Project documentation
```

## Contributing
Contributions, suggestions, and improvements are welcome and encouraged! If you would like the enhance any aspect of the project, such as analysis or visualisations:
1. Fork the repository
2. Create a feature branch
   ```bash
   git checkout -b feature/improve-analysis
3. Commit your changes
   ```bash
   git commit -m 'Add new visualisation'
4. Push to the branch
   ```bash
   git push origin feature/improve-analysis
5. Open a Pull Request

## Author
**Sam Lloyd**, sammy.lloyd@live.com, *github.com/lloydy-92*

## Acknowledgements
- zackthoutt on Kaggle for providing the dataset (*https://www.kaggle.com/datasets/zynicide/wine-reviews*).
- Codecademy Data Science Path for providing structured guidance on this project, as well as the dataset itself.
- The open-source community for libraries like ```pandas```, ```matplotlib```, and ```seaborn```.
------------------------------------------------------------------------------------------------------------------
"*Good data, like good wine, improves with careful analysis.*"
