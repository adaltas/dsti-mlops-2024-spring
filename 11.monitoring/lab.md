## 6. Data drift detection and model degradation

Today we will look at the example of model performance decay. We will be using library [evidently](https://evidentlyai.com/).

**Objectives:**

- See a concrete example of data drift.
- Learn how to detect and evaluate it.

**Depndencies:**

- notebook: `bicycle_demand_monitoring_tutorial.ipynb`. To make sure that you have the latest version, download it from [here](https://github.com/evidentlyai/evidently/blob/main/examples/data_stories/bicycle_demand_monitoring.ipynb).
- dataset: `train.csv`

**Instructions:**

1. Create the directory `monitoring`
2. Download the notebook and the dataset from `dependencies` to `monitoring`
3. Activate environment `env_mlops`
4. Install `evidently`: `pip install evidently`
5. Follow the tutorial [How to break a model in 20 days](https://evidentlyai.com/blog/tutorial-1-model-analytics-in-production)
