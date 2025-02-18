# DETIRE
Version 1.2

Authors: Yan Miao, Tianhong Dai

Maintainer: Yan Miao miaoyan@nefu.edu.cn

# Description
DETIRE (a hybrid Deep lEarning model for idenTifying vIral sequences fRom mEtagenomes) is a deep learning based virus identification method that could detect viruses directly from metagenomes. DETIRE is a two-stage architecture, containing a graph convolutional network (GCN) based sequence embedder and a two-path deep learning model. First, every sequence is cut into several 3-mer fragments, which are then successively input to the GCN-based sequence embedder to train the representations of all 3-mer fragments. After that, these embedded fragments are then fed into the CNN-path and BiLSTM-path to learn their features, respectively. Finally, by two dense layers and a softmax layer, a pair scores are generated, and the higher score determines which type the input sequence is. 

# Dependences
To utilize DETIRE on Windows, Python packages "sklearn", "numpy" and "matplotlib" are needed to be previously installed.

In convenience, download Anaconda from https://repo.anaconda.com/archive/, which contains most of needed packages.

To insatll Keras, start "cmd.exe" and enter <br>
```
pip install keras
```
Our codes were all edited by Python 3.6.5 with Keras 1.2.0.

# Usage
* Users can utilize the trained model in DETIRE directly to test users' query contigs.

  To make a prediction, users' own query contigs should be edited into a ".csv" file, where every line contains a single query contig. Run the file in https://github.com/crazyinter/Seq2Vec/blob/master/preprocessing.py to preprocess the testing datasets. And then run the codes below to give a set of scores (output as a .csv file) to each query contig. The first score represents the probability of the query sequence being virus, and the second score represents the probability of the query sequence being non-virus.
   ```
   from keras.models import load_model
   model = load_model('DETIRE_model.h5')
   y_pred = model.predict([X_test_rnn,X_test_cnn])
   np.savetxt('y_pred.csv', y_pred, delimiter = ',')  
   ```
* Users can also train DETIRE using your own training datasets.

  Run the file in https://github.com/crazyinter/Seq2Vec/blob/master/preprocessing.py to preprocess the training datasets. Then run the file "train_DETIRE.py" to train a new DETIRE model. the hyper-parameters can be set as your own experience or just use the default ones.
  TIPs: It will be Better to use Jupyter Notebook to run DETIRE.
  

# Copyright and License Information
Copyright (C) 2023 Northeast Forestry University

Authors: Yan Miao, Tianhong Dai

This program is freely available as Python at https://github.com/crazyinter/DETIRE.

Commercial users should contact Mr. Miao at miaoyan@nefu.edu.cn, copyright at Northeast Forestry University.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
