This repository contains the code for providing a service that offers real time detection of arrhythmia. Right now the work is under research.

**preprocess.ipynb**: preprocesses the ecg signal. Base noise and muscle artifact noise is removed using Butterworth filter and DWT (Discrete Wave Transform); two highest frequency bands and lowest 3 frequency bands are removed to focus only on the part of the signal that gives the most information. RR peaks are detected using neurokit library's ecg_process method. Data is further segmented around RR_Peaks with 49 data points to the left and 50 data points to the right of RR_Peaks. 

**model.ipynb**: extracts features using deep learning. Model is constructed using 4 CNN layers and 3 LSTM layers. Model is fed data in chunks of size 128.

**sig_info**: contains code of making a programmable hybrid deep learning model using mealpy's genetic algorithm. Parameters of models such as number of cnn layers, kernel size, hidden layer etc are passed in the search space of the algorithm to try and find the optimal configuration. Each time the algorithm figures a configuration the model is constructed and trained and evaluated and returns a fitness score which then helps the algorithm determine the competition between the generated models. This approach provides a mathematical foundation rather than a hit and trial experimentation approach. 
