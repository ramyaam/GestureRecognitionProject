# GestureRecognitionUsingDeepLearning
This project involves building a 3D Neural Network to correctly recognize hand gestures by a user to control a smart TV.

# Problem Statement:
The objective of this projects is to build a hand gesture recognition model that can be hosted on a camera installed in a smart TV that can understand 5 gestures.   
The gestures are continuously monitored by the webcam mounted on the TV. Each gesture corresponds to a specific command:  
-	Thumbs up:  Increase the volume  
-	Thumbs down: Decrease the volume  
-	Left swipe: 'Jump' backwards 10 seconds  
-	Right swipe: 'Jump' forward 10 seconds    
-	Stop: Pause the movie  

# About the Dataset: 
The training data consists of a few hundred videos categorised into one of the five classes. Each video (typically 2-3 seconds long) is divided into a sequence of 30 frames(images). These videos have been recorded by various people performing one of the five gestures in front of a webcam - similar to what the smart TV will use.  
The videos have two types of dimensions - either 360x360 or 120x160 (depending on the webcam used to record the videos).  

### Data Source : https://drive.google.com/uc?id=1ehyrYBQ5rbQQe6yL4XbLWe3FMvuVUGiL

# Summary of Nueral Network used and Result:
| Sr.No | Model & Parameters         | Data & Training Details                                      | Result & Decision                                                                 |
|-------|----------------------------|-------------------------------------------------------------|----------------------------------------------------------------------------------|
| 1     | Conv3D, Params: 144,421    | Images: 18, Size: 64x64, Epochs: 5, Time: 210 sec           | Train/Val Accuracy: 42%/41% (underfitting). Decision: Increase capacity (epochs, neurons). |
| 2     | Conv3D, Params: 144,421    | Images: 18, Size: 64x64, Epochs: 20, Time: 440 sec          | Train/Val Accuracy: 44%/44% (underfitting). Decision: Increase neurons, image size.       |
| 3     | Conv3D, Params: 288,101    | Images: 18, Size: 84x84, Epochs: 20, Time: 480 sec          | Train/Val Accuracy: 42%/41% (underfitting). Decision: Increase size, neurons, epochs.     |
| 4     | Conv3D, Params: 651,109    | Images: 18, Size: 100x100, Epochs: 30, Time: 750 sec        | Train/Val Accuracy: 58%/41% (overfitting). Decision: Reduce size, neurons, increase data. |
| 5     | Conv3D, Params: 181,285    | Images: 30, Size: 84x84, Epochs: 30, Time: 1,420 sec        | Train/Val Accuracy: 79%/66% (overfitting). Decision: Switch to other models.             |
| 6     | CNN-LSTM, Params: 1,657,445| Images: 30, Size: 120x120, Epochs: 20, Time: 900 sec        | Train/Val Accuracy: 91%/74% (overfitting). Decision: Reduce parameters.                  |
| 7     | CNN-LSTM, Params: 3,754,597| Images: 30, Size: 160x160, Epochs: 20, Time: 1,100 sec      | Train/Val Accuracy: 85%/80%. Decision: Reduce size, neurons.                             |
| 8     | CNN-LSTM, Params: 1,287,989| Images: 30, Size: 120x120, Epochs: 25, Time: 2,500 sec      | Train/Val Accuracy: 90%/79% (overfitting). Decision: Increase neurons.                   |
| 9     | CNN-LSTM, Params: 1,702,645| Images: 30, Size: 120x120, Epochs: 25, Time: 2,500 sec      | Train/Val Accuracy: 87%/82%. Decision: Explore GRU models.                               |
| 10    | CNN-LSTM + GRU, Params: 2,573,541| Images: 30, Size: 120x120, Epochs: 20, Time: 900 sec     | Train/Val Accuracy: 94%/79% (overfitting). Decision: Try transfer learning.              |
| 11    | MobileNet Transfer, Params: 3,840,453| Images: 18, Size: 120x120, Epochs: 5, Time: 600 sec   | Train/Val Accuracy: 91%/55% (poor performance). Decision: Train MobileNet weights.        |
| 12    | Transfer GRU, Params: 3,840,453| Images: 18, Size: 120x120, Epochs: 5, Time: 990 sec    | Train/Val Accuracy: 98%/95%. Decision: Final model selected due to high accuracy.         |


