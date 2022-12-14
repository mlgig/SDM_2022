# An Examination of Wearable Sensors versus Video Data Capture for Human Exercise Classification

Wearable sensors such as Inertial Measurement Units (IMUs) are often used to assess the performance of human 
exercise. Common approaches use handcrafted features based on domain expertise or automatically extracted features 
using libraries dedicated to time series analysis. Some recent techniques can also use directly the raw motion 
data. Usually, multiple sensors are required to achieve high classification accuracy, which is not very practical. 
Recent work utilizing the latest advances in computer vision applied to video has shown similar performance without
the need for manual feature engineering, while avoiding some pitfalls, such as sensor calibration and placement on 
the body, which may hinder the movement. In this paper, we compare the performance of wearable sensors using IMUs and 
video-based approaches for human exercise classification, on two real-world datasets consisting of Military Press and 
Rowing exercises. We compare the performance using a single camera that captures video in the frontal view versus using
the data captured by 5 IMUs placed on different parts of the body. We observe that a method based on a single camera can 
outperform a single IMU by 10 percentage points on average. Additionally, a minimum of 3 IMUs are required to outperform 
the single camera. We observe that working with the raw data using multivariate time series classifiers 
outperforms traditional approaches based on handcrafted or automatically extracted features. Finally, we show 
that an ensemble model combining the data from a single camera with a single IMU significantly outperforms either 
data modality. Our research opens up new and more realistic avenues for this application, where a  video using 
readily available smartphones combined with a single sensor can be used to more effectively classify human 
exercise execution.

![Alt text](figs/overview.png?raw=true)

<em>**Fig 1** Comparison of video (top) and sensors (bottom) to classify human exercise movement. The upper box presents
the process of obtaining multivariate data (only 3 out of 25 body parts shown) from video. The bottom box shows the raw 
Y signals from IMUs placed on the participant's body (only 3 signals shown here).</em>

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
not contain this file it can be copied from other folder as the order of the features remain same. The data can be 
downloaded from the Google Drive [link](https://drive.google.com/drive/folders/16grxbvok22cKgDIh2MkgOAznNNdpqPWO?usp=sharing). 

Please [email](mailto:ashish.singh@ucdconnect.ie) if you need access to the original videos.

## Comparison of IMUs, Video and Ensemble based approach
Data Source | Acc MP | Acc Rowing |
--------------- |--------|------------|
Placement of IMUs |        | |
3 IMUs (Wrists and Back)  | 0.91   | 0.80       |
1 IMU (RightWrist)    | 0.83   |  0.68      |
Video |        | | 
25 body parts         | 0.82   | 0.79|
8 body parts  | 0.88   | 0.83 |
Ensemble: video and IMUs  |        | |
Video (8 body parts) + 3 IMUs              | 0.93   | 0.88   |
Video (8 body parts) + 1 IMU RightWrist | 0.93   | 0.85 |

<em>Table 3: Comparison of accuracy obtained using IMUs and video for MP and Rowing. </em>

Table 3 presents the results for IMU and Video for both MP and Rowing exercises. We observe that a minimum of 3 IMUs 
are required to achieve a higher accuracy than a single video. A single video outperforms the accuracy of using a single
IMU for both exercises.

## Citation
Please cite this paper if it helped in your research:
```
@article{singh2021interpretable,
  title={Interpretable Classification of Human Exercise Videos through Pose Estimation and Multivariate Time Series Analysis},
  author={Singh, Ashish and Le, Binh Thanh and Le Nguyen, Thach and Whelan, Darragh and O???Reilly, Martin and Caulfield, Brian and Ifrim, Georgiana},
  year={2021},
  booktitle = {5th International Workshop on Health Intelligence(W3PHIAI-21) at AAAI21},
  publisher={Springer}
}


@misc{ashishdami2022,
  doi = {10.48550/ARXIV.2210.00507},
  url = {https://arxiv.org/abs/2210.00507},
  author = {Singh, Ashish and Bevilacqua, Antonio and Nguyen, Thach Le and Hu, Feiyan and McGuinness, Kevin and OReilly, Martin and Whelan, Darragh and Caulfield, Brian and Ifrim, Georgiana},
  year={2022},
  title = {Fast and Robust Video-Based Exercise Classification via Body Pose Tracking and Scalable Multivariate Time Series Classifiers},
}
```