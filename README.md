This repository contains the code for providing a service that offers real time detection of arrhythmia. 

**preprocess.ipynb**: preprocesses the ecg signal. Base noise and muscle artifact noise is removed using Butterworth filter and DWT (Discrete Wave Transform); two highest frequency bands and lowest 3 frequency bands are removed to focus only on the part of the signal that gives the most information. RR peaks are detected using neurokit library's ecg_process method. Data is further segmented around RR_Peaks with 199 data points to the left and 200 data points to the right of RR_Peaks. 

**model.ipynb**: extracts features using deep learning. Model is constructed using 4 CNN layers and 3 LSTM layers. Model is fed data in chunks of size 2500 with step size of 1250(50% overlap).
