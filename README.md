# PhyaatDataset 
Phyaat Database

---
title: dataset
layout: base
---

# Homepage - https://PhyAAt.github.io/
# PhyAAt Dataset

<h2 class="no-bg">Description</h2>
<div style="text-align: justify">
The dataset contain three physiological signals recorded at sampling rate of 128Hz from 25 healthy subjects during the experiment. Electroenceplogram (<b>EEG</b>) signal is recorded using a 14-channel Emotiv Epoc device. Two signal streams of Galvanic Skin Response (<b>GSR</b>) were recorded, instantnious sample and moving averaged signal. From photoplethysmogram (<b>PPG</b>) sensor (pulse sensor), a raw signal, inter-beat interval (IBI), and pulse rate were recorded. All the signals were properly labeled. A short segment of recorded signals are shown in Figure-1.<br>
EEG Channels: 'AF3', 'F7',  'F3',  'FC5', 'T7',  'P7', 'O1', 'O2', 'P8', 'T8', 'FC6', 'F4', 'F8', 'AF4'
</div>

<img class="center" alt="Segment of signals" src="https://PhyAAt.github.io/assets/images/SegmentOfSignalsV6.jpg" width="60%">
                                                                                                                             
<figcaption>Fig. 1: A short segment of recorded signals and labels</figcaption>

<h2 class="no-bg">File structure and field names in files</h2>
As shown in figure below, The dataset contain 25 directories, one for each subject. Each directory contain Signals.csv and Textscores.csv files.

<figure>
<img style="float: right;" alt="Dataset structure" src="https://PhyAAt.github.io/assets/images/Dataset.png" width="30%">
</figure>


**Signal File**<br>
Signals.csv file contain all the 19 streams of signals and lebels. Following are coulumn names
* **TimeStamp** : Time stamp - normalize to start with 00 Hour
* **'AF3' ..'AF4'** : 14 Channels of EEG Signals
* **PPG** : Raw PPG signal
* **BPM** : Pulse Rate in Beats per minute
* **IBI** : Inter-Beat-Interval
* **0**   : Zero (Just a divider for alignment)
* **gsrRaw** : instantnious GSR signal
* **gsrLPF** : Lowpass GSR Signals (Moving averaged of past 100 samples)
* **Label_N**: Noise Levels [-6,-3,0,3,6,1000] dB
* **Label_S**: Semanticity Label: 0-Semantic, 1-Non-semantic
* **Label_T**: Task: 0-Listenting, 1-Writing, 2-Resting
* **CaseID** : CaseID An identyfier code for experimental condition, encoded value of noise level and semanticity

**Labels and CaseID** also include **value -1**, for the signals before first listening task started

**Textscore file**<br>
Textscore file contain, TimeStamp, Attention Score (Correctness Score), Total Words and CorrectWords, along with CaseID, SNR and Semanticity Label for each listening segment. The number of attention scores and number of listening segments are same. At very few occasions, due to bad connection recording of physiological signals were dropped, so a very few segments among all the subjects might not have sufficient samples to process but they still have attention score and other labels.



<h2 class="no-bg">Download the dataset</h2>

**Python** <br>
To download the dataset, install phyaat library and download through it.

```consol
pip install phyaat
```
```python
import phyaat as ph

# to download dataset of subject 1 in given path 'dirpath'
dirPath = ph.download_data(baseDir='../PhyAAt_Data', subject=1,verbose=0,overwrite=False)

# to download dataset of all the subjects
dirPath = ph.download_data(baseDir='../PhyAAt_Data', subject=-1,verbose=0,overwrite=False)
```
**[CHECK THE STARTER GUIDE](/introduction)**

**Manually**<br>
If you are using other programming framework such as matlab or R, Download dataset manually from [**Github repository**](https://github.com/Nikeshbajaj/PhyaatDataset) and extract all the csv files.



<h2 class="no-bg">Download tabular data for statistical analysis</h2>
For statistical analysis of attention score with auditory conditions, download a compiled datasheet as csv file.
<!-- https://nikeshbajaj.github.io/PhyaatDataset/PhyAAt_AttentionScoreData_v1.csv -->
* <h3><a href="https://nikeshbajaj.github.io/PhyaatDataset/PhyAAt_AttentionScoreData_v1.csv" target="_blank">Download Tabular Data File</a></h3>

File structure is as follow;

| SID | SNRdB | Semanticity | LengthStim  | AttentionScore |
| ----------- | ----------- | ----------- | -----------  |
| S1 | -6 | 1	| L3	| 11.18881119 |
| S3 | 1000 | 0	| L2	| 86.16071429 |
| S5 |  6 | 0	| L2	| 75 |


Here:
* **SID**   : Subject ID, S1 .. S25
* **SNRdB** : Noise Level in dB, -6,-3,0,3,6, 1000. Here 1000 is for noise free
* **Semanticity**: Semanticity, 0-Semantic, 1-Non Semantic
* **LengthStim**: Length of stimulus, L1-small, L2-medium, and L3-long
* **AttentionScore**: Average Attention score for given condition (average score of multiple stimuli in same auditory condition). Attention score ranges from 0 to 100, as a level of attention.

In addtion, a file with demographics and self rating of language can be download too.

* <h4><a href="https://nikeshbajaj.github.io/PhyaatDataset/PhyAAt_Demographic_Rating_v1.csv" target="_blank">Download Demographic Data File</a></h4>


<!--
  <div class="section" id="experiment">
  <h1>Dataset<a class="headerlink" href="#experiment" title="Permalink to this headline">¶</a></h1>
  <div class="section" id="institutions">

  <h2>Dataset<a class="headerlink" href="#institutions" title="Permalink to this headline">¶</a></h2>
  <img alt="Segment of signals" src="{{ "/assets/images/SegmentOfSignalsV2.png" | relative_url }}" width="40%">
  <img alt="Dataset structure" src="{{ "/assets/images/Database.png" | relative_url }}" width="30%">

  <h2>Signals<a class="headerlink" href="#institutions" title="Permalink to this headline">¶</a></h2>


  <h2>Under construction..<a class="headerlink" href="#institutions" title="Permalink to this headline">¶</a></h2>
<p>This ...:</p>
  <a><img alt="Under construction" src="{{ "/assets/images/Underconstruction.png" | relative_url }}" width="300"></a>

  </div>

  </div>
-->
