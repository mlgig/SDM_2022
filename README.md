# An Examination of Wearable Sensors versus Video Data Capture for Human Exercise Classification

Wearable sensors such as Inertial Measurement Units (IMUs) are often used to assess the performance of human 
exercise. Common approaches use handcrafted features based on domain expertise or automatically extracted features 
using libraries dedicated to time series analysis. Some recent techniques can also use directly the raw motion 
data. Usually, multiple sensors are required to achieve high classification accuracy, which is not very practical. 
Recent work utilizing the latest advances in computer vision applied to video has shown similar performance without
the need for manual feature engineering, while avoiding some pitfalls, such as sensor calibration and placement on 
the body, which may hinder the movement. In this paper, we compare the performance of wearable sensors using IMUs and video-based approaches for human 
exercise classification, on two real-world datasets consisting of Military Press and Rowing exercises. We compare 
the performance using a single camera that captures video in the frontal view versus using the data captured by 
5 IMUs placed on different parts of the body. We observe that a method based on a single camera can outperform 
a single IMU by 10 percentage points on average. Additionally, a minimum of 3 IMUs are required to outperform 
the single camera. We observe that working with the raw data using multivariate time series classifiers 
outperforms traditional approaches based on handcrafted or automatically extracted features. Finally, we show 
that an ensemble model combining the data from a single camera with a single IMU significantly outperforms either 
data modality. Our research opens up new and more realistic avenues for this application, where a  video using 
readily available smartphones combined with a single sensor can be used to more effectively classify human 
exercise execution.


## Data Description
The data used is the video recordings and IMU data of the execution of the Military Press (MP) and Rowing exercise.
Participants completed 10 repetitions of the normal form and 10 repetitions with induced deviations. We employ two 
different ways to classify IMU and video data: 
- Time series way
- Automated feature extraction

Raw data from IMUs can be treated as multivariate time series with multiple diemsions. Similarly, for video we 
obtain multivariate time series by repeatedly applying OpenPose as human pose estimation library to track 25 body
parts of a human body over all the frames.
The TSC folder contains the data in time series for both IMUs and videos.  The data shared in this repository in 
data folder here is already pre-processed i.e. it is segmented, re-sampled to a length of 161 and split into a 
ration of 70/30 for train/test.
Folder Manual contains features extracted using domain knowledge for IMUs in the tabular form. Folder Automated
contains tabular features created using libraries such as catch22 and tsfresh 
For tabular features, also train/test has already been created in the ratio of 70/30 for train/test. Some folders 
contain the pid file which basically maps each sample in the train/test to a unique participant id with a particular
exercise type and repetition number. This information can be used to create further splits. If some folders does
not contain this file it can be copied from other folder as the order of the features remain same.

Please [email](mailto:ashish.singh@ucdconnect.ie) if you need access to the original videos.



## Citation
Please cite this paper if it helped in your research:
```
@article{singh2021interpretable,
  title={Interpretable Classification of Human Exercise Videos through Pose Estimation and Multivariate Time Series Analysis},
  author={Singh, Ashish and Le, Binh Thanh and Le Nguyen, Thach and Whelan, Darragh and O’Reilly, Martin and Caulfield, Brian and Ifrim, Georgiana},
  year={2021},
  booktitle = {5th International Workshop on Health Intelligence(W3PHIAI-21) at AAAI21},
  publisher={Springer}
}
```