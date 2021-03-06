# Skoltech Deep Learning course project 2020
# Convolutional RNNs for Portfolio Investments of Cryptocurrencies using Order Book Data

Team members: Aiusha Sangadiev, Kirill Stepanov, Andrey Poddubny, Kirill Bubenchikov, Nikita Bekezin.

This repository contains code related to the project report, and also the FI-2010 dataset with a link to download the cryptocurrency dataset (it was too big to be uploaded on github).

# Setup and Dependencies

+ Python3
+ Numpy, pandas, scipy
+ Matplotlib
+ PyTorch
+ Weights & Biases (https://pypi.org/project/wandb/)

Setup:
1) download the files;
2) download FI-2010.zip dataset and unpack into 'FI-2010' folder in the same location as the project, otherwise change data paths when necessary in the Jupyter notebooks to correctly load the files;
3) download the crypto_data.zip dataset from Google Disk - https://drive.google.com/file/d/1ds6CB_tPeGoUU5Hd4XU12e91YnNTOqHT/view?usp=sharing , unpack into the 'crypto_data' folder or change data paths in the Jupyter notebooks;
4) download the data necessary for the portfolio optimization from Google Disk - https://drive.google.com/file/d/1ThS9O2ILrbR76RU7JJQN1zXPPUV4ooBp/view?usp=sharing , unpack into the 'portfolio_data' folder or change data paths in the notebooks.

P.S. If using in colab, please change AUX_DATA_ROOT to fit your path structure on the Drive.

# Content

1) FI-2010.zip - FI-2010 dataset used in this work;
2) Folder 'sota_models' contains DeepLOB and DeepResLOB models;
3) Folder 'weights' contains weights for all three classification experiments (FI-2010, two setups for cryptocurrency) with different prediction horizons for DeepLOB and DeepResLOB models, in addition to that in subfolder 'portfolio' there are weights for the LSTM portfolio allocation model trained with three different loss functions;
4) Binance_API_dataset.ipynb, Data_preprocessing.ipynb - Jupyter notebooks showing how we performed the collection of data through Binance API and the preprocessing steps described in the report (some operations there require mounted Google Drive and redoing it takes several hours \ days, since there are gigabytes of data and API is rather slow);
5) CNN_LSTM_baseline.ipynb - baseline models and code showing how training process was performed for them;
6) train_deep.py - training and testing code for the DeepLOB and DeepResLOB models;
7) dataset_wrapper.py - PyTorch Dataset wrappers around the data;
8) Portfolio.ipynb - code of the portfolio optimization part and related experiments;
9) DeepResLOB_exp.ipynb - experiments (FI-2010, both token setups) for DeepLOB and DeepResLOB;
10) Folder 'images' contains images used in this README.

# Model architecture - DeepResLOB

![](/images/deep_res_lob.png)

The full description of the model and its architecture is provided in the report.

# Results

Solved some of the DeepLOB problems:
1) Reduced sensitivity to weights allocation:

![](/images/exp1.PNG)

2) Faster and better convergence:

![](/images/exp2.PNG)

Thorough comparison of DeepResLOB against DeepLOB and two baseline CNN & LSTM models can found in the report.

Portfolio optimization results:

![](/images/ready_markowitz.jpg)

It can be seen, that the proposed approach performs the best when using maximum drawdown (MDD) as a loss function.
