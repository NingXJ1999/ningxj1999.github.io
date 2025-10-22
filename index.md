# REFED-Dataset

**REFED: A Subject Real-time Dynamic Labeled EEG-fNIRS Synchronized Recorded Emotion Dataset**

## About REFED

The REFED is the first emotional brain-computer interface dataset integrating multimodal brain signals and real-time dynamic emotion annotation, fills a critical gap in the study of neural mechanisms of emotional dynamic evolution and the development of high-reliability aBCI models. By synchronizing the acquisition of EEG and fNIRS signals, REFED realizes the joint observation of neuroelectrical activity and hemodynamic response under emotional evocation, which provides unique data support for exploring emotion-related neuro-vascular coupling mechanisms. Meanwhile, the dynamic potency and arousal annotation based on subjects' subjective reports, for the first time, realizes millisecond-level temporal alignment of brain signals with emotional state changes, which significantly improves the temporal modeling capability of the emotion recognition model. Experimental validation shows that the dataset meets the standard in terms of emotion evoked validity and labeling reliability, and the multimodal signal features show significant correlation with the dynamic labeling. The open sharing of REFED will promote the cross-modal neural representation parsing for the dynamic encoding of emotions in the following research directions, and lay an important foundation for the field of affective computation and brain-computer interfaces to move towards dynamic interaction paradigms with higher ecological validity.

## Data overview

```plaintext
REFED/
├── README.md
├── Metadata.csv
├── SAM.csv
├── PANAS.csv
├── fNIRS_reservations.csv
├── fNIRS_coordinate.csv
├── data/
│   ├── 1/
│   │   ├── EEG_baselines.mat
│   │   ├── EEG_videos.mat
│   │   ├── fNIRS_baselines.mat
│   │   └── fNIRS_videos.mat
│   ├── 2/
│   │   └── ...
│   └── 32/
│       └── ...
└── annotations/
    ├── 1_label.mat
    ├── 2_label.mat
    └── ... (up to 32_label.mat)

```

### 📄 README.md

Documentation of instructions for using the dataset, including background, structure, data collection, license agreement, etc.

### 📄 Metadata.csv

Subject basic information (ID, gender, age, health status, etc.).

### 📄 SAM.csv

Post-trial subjective mood scores based on the Self-Assessment Manikin (SAM) scale (valence and arousal).

### 📄 PANAS.csv

Positive and Negative Affect Self-Assessment Results Before and After the Experiment (Positive and Negative Affect Schedule).

### 📄 fNIRS_reservations.csv

fNIRS data acquisition logs, including bad channel markers.

### 📄 fNIRS_coordinate.csv

3D coordinates of the fNIRS channels for alignment and spatial analysis.

------

### 📁 data/

Contains folders of data for subjects numbered 1 through 32, each containing the following raw brain signal files:

**Subdirectory structure:**

```
data/{subject_id}/
├── EEG_baselines.mat       # Resting EEG signal (baseline phase)
├── EEG_videos.mat          # Emotionally evoked phase EEG signaling (video stimulation)
├── fNIRS_baselines.mat     # Resting-state fNIRS signal (baseline phase)
└── fNIRS_videos.mat        # Emotionally evoked phase fNIRS signaling (video stimulation)
```

- Each subject corresponds to a numbered folder, for a total of 32 subjects.
- EEG sampling rate of 200 Hz, fNIRS sampling rate of 47.62 Hz.
- fNIRS has six signal types, including HbO, HbR, HbT, Abs 780 nm, Abs 805 nm, Abs 830 nm.
- `.mat` format saves multi-trial time series data, such as video_1, a total of 15 videos.
-  The shape of EEG is channel dimension * time dimension and the shape of fNIRS is signal type * channel dimension * time dimension.

------

### 📁 annotations/

Store **the real-time dynamic labeling data** of each subject during the viewing of the emotion video:

```
annotations/
├── 1_label.mat
├── 2_label.mat
└── ... (up to 32_label.mat)
```

- Each *_label.mat file contains the results of subjects' subjective labeling of emotions based on the joystick. Contains both valence and arousal dimensions.
- Annotation sequences containing changes in valence and arousal over time have been precisely aligned to brain signals (shaped as 2 * time dimension). 

## Collection

The channel distribution of the joint EEG-f NIRS acquisition is shown in the following figure.

<img src="./Figures/Figure_1.png" alt="Figure_1" style="zoom:50%;" />

In order to realize the real-time annotation of subjects' emotional state and the automated control of the whole process, we also developed a real-time annotation and control system, as shown in the following figure.

![图片2](./Figures/Figure_2.png)

## License

Publicly available under the `CC BY-NC-SA` protocol, with direct access to users after confirming use for non-commercial research purposes. 
