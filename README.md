#  Kaggle Challenge: CVOID-19 Global Forecasting

Please Visit the [Kaggle Page for COVID 19 Global Forecasting](https://www.kaggle.com/c/covid19-global-forecasting-week-2/overview) for more information about the contest.

Some useful Kaggle discussion:
* [Thread for Sharing datasets](https://www.kaggle.com/c/covid19-global-forecasting-week-1/discussion/137078)
* [Summary of Prediction models](https://www.kaggle.com/c/covid19-global-forecasting-week-1/discussion/137796)

## Getting started

### Setting up environment

Install latest [Anaconda Distribution](https://www.anaconda.com/distribution/#download-section)

```bash
conda remove -y --name kaggle-covid --all
conda create -n kaggle-covid -y python=3.7 pandas numpy scipy statsmodels scikit-learn matplotlib seaborn ipykernel
conda activate kaggle-covid
conda install -y -c pyviz holoviews bokeh
pip install autopep8
ipython kernel install --user --name=kaggle-covid
conda deactivate
conda activate base
jupyter notebook --notebook-dir="./" --NotebookApp.port=8888
```

## Kaggle Competition Rules
The Competition Rules can be found in the link below. It is important to know the competition permits the use of both competition and external data. As described in the rules section on the Kaggle competition page, the external data has to be published on the official competition forum before the entry deadline. As for this particular challenge, the entry deadline is on the same day as the submission deadline, which is on March 25th. We don’t have to rush for the first-week entry. However, please keep in mind any external data we found or generated must be posted before the deadline.
Also, if you decided to contribute to the competition, make sure you join the team before March 25th for the first-week competition. 

Kaggle docs:
https://www.kaggle.com/docs

## Datasets

### Completed datasets

* [Kaggle COVID-19 data](https://www.kaggle.com/c/covid19-global-forecasting-week-1/data)
* [Population of cities](https://www.kaggle.com/dgrechka/covid19-global-forecasting-locations-population)
    * ~~Other source: https://data.london.gov.uk/dataset/global-city-population-estimates~~
* [Number of ICU beds](https://www.kaggle.com/jaimeblasco/icu-beds-by-county-in-the-us)
* [Number of Physicians per ppl by Country](https://en.wikipedia.org/wiki/List_of_countries_and_dependencies_by_number_of_physician)
* Regional Demographics, like population by age group
    * Media age from [kaggle/koryto](https://www.kaggle.com/koryto/countryinfo), amongst other things.
* [Airport and Routes (Private dataset, see below*)](https://openflights.org/data.html)

### Uncollected / Unfinished datsets

* Social Media
    * twitter data (we need API access)
    * (distribution of) sentiment by geography
    * visits to CSSE ArcGIS Portal (https://github.com/CSSEGISandData/COVID-19), ask jhusystems@gmail.com for website visit data
* Policies
    * ideally, we would know how much people are going out?
* Treatment Options
    * Vaccine trial stages


*All datasets from Kaggle are found on the [sharing datasets public discussion board](https://www.kaggle.com/c/covid19-global-forecasting-week-1/discussion/137078). All "private" external datasets should be entered on that discussion board.


## Relevant Readings

### Papers

* https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2305771/
* https://www.sciencedirect.com/science/article/pii/S0013935115300128
* https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0088075

### Guides

* Very Short and Long Time Series: https://otexts.com/fpp2/long-short-ts.html
* Evaluating Time-series Forecasting: https://otexts.com/fpp2/accuracy.html
* https://towardsdatascience.com/how-not-to-use-machine-learning-for-time-series-forecasting-avoiding-the-pitfalls-19f9d7adf424: 
> "Defining the model to predict the difference in values between time steps rather than the value itself, is a much stronger test of the models predictive powers."
* ARIMA with Python: https://machinelearningmastery.com/arima-for-time-series-forecasting-with-python/


## Our methods

Methods are preliminary, final approach will depend on how models perform.

### Clustered Time Series

1. Clustering cities and countries
    * type of response
    * healthcare system
    * transportation (air travel)
    * population density 
    * etc...
2. Train time-series models by cluster
    * train on difference in value
    * evaluate against historical mean
    * this help us separate cities/countries with different environment and response
3. Combine model predictions

### LSTM Neural Network

TBD

### Hybrid Gradient Boosting Tree and LSTM

TBD

### Spatio-Temporal Neural Networks
