# Speaker Identification & Verification with GMM-MFCC

This project implements a **speaker identification and verification system** using **Gaussian Mixture Models (GMM)** and **Mel-Frequency Cepstral Coefficients (MFCC)**.  


## Overview
- **Goal:** Distinguish and authenticate speakers by their unique vocal characteristics.  
- **Key Idea:** Extract MFCC features from audio signals, remove silence with Voice Activity Detection (VAD), and train a GMM per speaker to model acoustic patterns.

## Dataset
- **Speakers:** 23 total (10 male, 13 female).  
- **Training:** ~2 minutes of speech per speaker.  
- **Testing:** 5 s, 10 s, and 15 s audio segments (5 samples per duration).  
- Includes silence and background noise to evaluate robustness.

## Methodology
1. **Pre-processing:** Resample to 16 kHz, apply VAD to remove silences.  
2. **Feature Extraction:** 13-dimensional MFCCs (first coefficient dropped to reduce noise).  
3. **Modeling:** Train a GMM for each speaker with varying numbers of Gaussian components (8–256).  
4. **Evaluation:**  
   - *Identification:* Choose the speaker model with highest likelihood.  
   - *Verification:* Compare likelihood to a threshold (Equal Error Rate criterion).

## Results
- **Optimal setup:** 64 Gaussian components with 15 s test segments.  
- **Accuracy:** > 90 % identification for 15 s samples; performance drops with shorter clips.  
- **Trade-offs:** More components improve accuracy up to ~128; beyond that gains are marginal and risk overfitting.

## Key Takeaways
- Longer audio segments provide more reliable identification.  
- Proper silence removal significantly enhances model consistency.  
- GMM-MFCC remains a strong baseline for speaker recognition tasks.
