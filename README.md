# Arrythmia_Classification

## Introduction

The 2017 PhysioNet/CinC Challenge aims to encourage the development of algorithms to classify, from a single short ECG lead recording (between 30 s and 60 s in length), whether the recording shows normal sinus rhythm, atrial fibrillation (AF), an alternative rhythm, or is too noisy to be classified.

There are various types of cardiac arrhythmias that may be classified by:


- Origin: atrial arrhythmia, junctional arrhythmia, or ventricular arrhythmia.
- Rate: tachycardia ( > 100 beats per minute (bpm) in adults) or bradycardia ( < 60 bpm in adults).
- Mechanism: automaticity, re-entry, triggered.
- AV Conduction: normal, delayed, blocked.
- Duration: non-sustained (less than 30 s) or sustained (30 s or longer).


AF is defined as a “tachyarrhythmia characterized by predominantly uncoordinated atrial activation with consequent deterioration of atrial mechanical function” by the American College of Cardiology (ACC), the American Heart Association (AHA) and the European Society of Cardiology (ESC) [1]. AF is the most common sustained cardiac arrhythmia, occurring in 1-2% of the general population [2; 3] and is associated with significant mortality and morbidity through association of risk of death, stroke, hospitalization, heart failure and coronary artery disease, etc. [3; 4]. More than 12 million Europeans and North Americans are estimated to suffer from AF, and its prevalence will likely triple in the next 30-50 years [5]. More importantly, the incidence of AF increases with age, from less than 0.5% at 40-50 years of age, to 5-15% for 80 year olds [6].

Despite the enormity of this problem, AF detection remains problematic, because it may be episodic. AF detectors can be thought of belonging to one of two categories: atrial activity analysis-based or ventricular response analysis-based methods. Atrial activity analysis-based AF detectors are based on the analysis of the absence of P waves or the presence of fibrillatory f waves in the TQ interval. Published methods to do this include: an echo state neural network [7], P-wave absence (PWA) based detection [8], analysis of the average number of f waves [9], P-wave-based insertable cardiac monitor application [10], wavelet entropy [11] [12] and wavelet energy [13]. Atrial activity analysis-based AF detectors can achieve high accuracy if the recorded ECG signals have little noise contamination and high resolution, but tend to suffer disproportionately from noise contamination [4]. In contrast, ventricular response analysis is based on the predictability of the inter-beat timing (‘RR intervals’) of the QRS complexes in the ECG. RR intervals are derived from the most obvious large amplitude feature in the ECG, the R-peak, the detection of which can be far more noise resistant. This approach may therefore be more suitable for automatic, real-time AF detection [14]. Published methods include: Poincaré plot analysis [15], Lorenz plot analysis [16], analysis of cumulative distribution functions [17], thresholding on the median absolute deviation (MAD) of RR intervals [18], histogram of the first difference of RR intervals [19], minimum of the corrected conditional entropy of RR interval sequence [20], 8-beat sliding window RR interval irregularity detector [21], symbolic dynamics and Shannon entropy [22], sample entropy of RR intervals [23; 24; 25], and normalized fuzzy entropy of RR intervals [26].

It is worth noting that AF detectors that combine both atrial activity and ventricular response could provide an enhanced performance by combining independent data from each part of the cardiac cycle. Such detection approaches have included: RR interval Markov modeling combined with PR interval variability and a P wave morphology similarity measure [27] and a fuzzy logic classification method which uses the combination of RR interval irregularity, P-wave absence, f-wave presence, and noise level [28]. It is also worth noting that multivariate approaches based on machine learning that combines several of the above single features can also provide enhanced AF detection [29; 30; 31].

Previous studies concerning AF classification are generally limited in applicability because 1) only classification of normal and AF rhythms were performed, 2) good performance was shown on carefully-selected often clean data, 3) a separate out of sample test dataset was not used, or 4) only a small number of patients were used. It is challenging to reliably detect AF from a single short lead of ECG, and the broad taxonomy of rhythms makes this particularly difficult. In particular, many non-AF rhythms exhibit irregular RR intervals that may be similar to AF. In this Challenge, we treat all non-AF abnormal rhythms as a single class and require the Challenge entrant to classify the rhythms as 1) Normal sinus rhythm, 2) AF, 3) Other rhythm, or 4) Too noisy to classify.


https://physionet.org/content/challenge-2017/1.0.0/

| Type   | # Recordings   | Mean (s) | SD (s) | Min (s) | Median (s) | Max (s) |
|--------|----------------|----------|--------|---------|------------|---------|
| Normal |      5154      |     31.9 |  10.0  |   61.0  |    30.0    |   9.0   |
| AF     |      771       |     31.6 |	12.5	|   60	  |    30	     |   10.0  |
| Noisy  |      2557      |     34.1 |  11.8  |   60.9  |    30	     |   9.1   |
| Other  |      46        |     27.1 |	9.0   |	  60    |	   30	     |   10.2  |
| Total  |      8528      |     32.5 |	10.9	|   61.0  |    30      |	 9.0   |

## Model Used

The model used is inpsired of Classification of ECG Arrhythmia using Recurrent Neural Networks by Shraddha Singh Saroj, Kumar Pandey, Urja Pawar, Rekh Ram Janghel. It consist of 3 LSTM layers of respectively 64,256 and 100 neurons with a dropout rate of 0.2. 

Sequences needed to be padded, because of the dissimilarity of sequence lengths and can not be handled within a ragged tensor.

The model is implemented with TensorFlow. 

## Results

