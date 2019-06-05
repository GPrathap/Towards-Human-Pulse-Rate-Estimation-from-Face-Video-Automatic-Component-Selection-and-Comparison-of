<a href=""><img src="https://img.shields.io/badge/download%20paper-PDF-ff69b4.svg" alt="Download paper in PDF format" title="Download paper in PDF format" align="right" /></a>
<a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT licensed" title="MIT licensed" align="right" /></a>

## Towards Human Pulse Rate Estimation from Face Video: Automatic Component Selection and Comparison of Blind Source Separation Methods https://arxiv.org/abs/1810.11770 
> ###### Table of Contents
>
>  * [Abstract](#Abstract)
>  * [Overview](#Overview)
>  * [Dataset](#Dataset)
>  * [Results](#Results)
>  * [Running the Project](#Running)
>  * [Citing](#citing)

### Abstract
Human heartbeat can be measured using several
different ways appropriately based on the patient condition which
includes contact base such as measured by using instruments and
non-contact base such as computer vision assisted techniques.
Non-contact based approached are getting popular due to those
techniques are capable of mitigating some of the limitations of
contact-based techniques especially in clinical section. However,
existing vision guided approaches are not able to prove high
accurate result due to various reason such as the property of
camera, illumination changes, skin tones in face image, etc. We
propose a technique that uses video as an input and returns pulse
rate in output. Initially, key point detection is carried out on
two facial subregions: forehead and nose-mouth. After removing
unstable features, the temporal filtering is applied to isolate
frequencies of interest. Then four component analysis methods
are employed in order to distinguish the cardiovascular pulse
signal from extraneous noise caused by respiration, vestibular
activity and other changes in facial expression. Afterwards,
proposed peak detection technique is applied for each component
which extracted from one of the four different component
selection algorithms. This will enable to locate the positions
of peaks in each component. Proposed automatic components
selection technique is employed in order to select an optimal
component which will be used to calculate the heartbeat.

### Overview
Sequence of steps of proposed methodology how pulse rate is calculated from a facial video
<p align="center"><img src="images/project_schema.png" alt="Sequence of steps of proposed methodology how pulse rate is calculated from a facial video"/></p>


### Steps
1. Face Detection & Feature Tracking
<p align="center"><img src="images/facenfeatures.png" alt="Face Detection & Feature Tracking"/></p>

2. Normalized extracted components from JADE algorithm and the result of applying the SSA on each component
<p align="center"><img src="images/withandwithoutssa.png" alt="Normalized extracted components from JADE algorithm and the result of applying the SSA on each component"/></p>

3. Motions of interest corresponding to each component
<p align="center"><img src="images/motion_of_interest.png" alt="Motions of interest corresponding to each component"/></p>

4. This figure shows the peak detection of the result of the MDTW. The horizontal axis represents Pos_v and the
vertical axis represents values of Dis_v . A predefined threshold value is used to control the number of detection points.
<p align="center"><img src="images/peakdetection.png" alt="MDTW results"/></p>

5. The figure shows that locations of peak points which correspond to the component that is chosen form ACS. In
this case, the 5th component was selected and then it is used to locate the peak points of original components which were
extracted from the JADE algorithm
<p align="center"><img src="images/labeld_component.png" alt="Face Detection & Feature Tracking"/></p>

### Dataset
Dataset can be download form here : https://github.com/vladostan/Dataset-for-video-based-pulse-detection

Initial data matrix y (size NxM), where: N = number of feature points, M = number of frames (time in seconds * fps)

Interpolated data matrix y_filtered (N*cM): Applied cubic spline interpolation from 'fps' Hz to samplingRate Hz, c = samplingRate/fps

Stable data matrix y_stable (aN*cM): Some unstable feature points are removed, 0 < a < 1

Filtered data matrix y_filtered (aN*cM): Butterworth 5th filter applied

Component Analysis matrix y_xxx (b*cM): b = number of desired extracted components (default = 5)

### Results
<p align="center"><img src="images/result1.png" alt="pulse rate estimation"/></p>
<p align="center"><img src="images/result2.png" alt="rmse"/></p>

### Running

processData.m can be used to extract independent components for a given video
Configurations needs to be changed appropriately in ACS.py and before running the ACS.py. 

### Citing

If you find this paper useful in some way, you can cite it with the following BibTeX entry:
## @INPROCEEDINGS{8710532, 
author={V. {Ostankovich} and G. {Prathap} and I. {Afanasyev}}, 
booktitle={2018 International Conference on Intelligent Systems (IS)}, 
title={Towards Human Pulse Rate Estimation from Face Video: Automatic Component Selection and Comparison of Blind Source Separation Methods}, 
year={2018}, 
volume={}, 
number={}, 
pages={183-189}, 
keywords={blind source separation;cardiovascular system;computer vision;electrocardiography;face recognition;feature extraction;higher order statistics;independent component analysis;medical signal processing;patient monitoring;principal component analysis;face video datasets;blind source separation methods;human heartbeat;patient condition;contact base;noncontact base;computer vision assisted techniques;contact-based techniques;clinical section;illumination changes;skin tones;face image;key point detection;facial subregions;component analysis methods;cardiovascular pulse signal;facial expression;automatic components selection technique;optimal component;peak detection technique;human pulse rate estimation;vision guided approaches;Face;Feature extraction;Heart beat;Principal component analysis;Electrocardiography;Pulse measurements;Blind source separation;video-based pulse detection;face feature tracking;component analysis;automatic component selection;moving dynamic time warping;singular spectral analysis}, 
doi={10.1109/IS.2018.8710532}, 
ISSN={1541-1672}, 
month={Sep.},}
