#  Interpretable Electrode-Band Optimization for Affective Emotion Decoding.

### Detailed Overview of Findings

This study presents a comprehensive framework for EEG-based emotion recognition that reduces computational complexity, offering an efficient Solution for real-time emotion recognition in neurotechnology applications by leveraging explainable deep learning techniques and cross-dataset validation. This study incorporates an explainable AI framework employing SHapley Additive exPlanations (SHAP) to identify the most informative electrodes and frequency bands for emotion decoding, so that the input parameters of the prediction model can be reduced, thereby decreasing prediction complexity. Using the DEAP dataset, which includes EEG recordings from 32 participants across 32 electrodes and 8 additional physiological signals (such as electrooculogram, electromyogram, and respiration), the study aimed to decode four core emotional dimensions: arousal (intensity of emotion or alertness), valence (pleasantness of the emotion), dominance (control or influence over the emotion), and liking (subjective preference or enjoyment). For cross-dataset generalization, SEED-V and AMIGO datasets were also used in this study.

  1. Frequency Domain Transformation for Structured Modeling
     
    To prepare the raw EEG data for machine learning, the signals were first transformed from the time domain into the frequency domain using the Fast Fourier Transform (FFT). This enabled the extraction of five canonical frequency bands (Theta, Alpha, Low Beta, High Beta, and Delta) per electrode, resulting in a structured tabular format. This transformation not only enabled compatibility with traditional models but also preserved meaningful spectral patterns critical for emotion decoding.
    
  2. Modeling: Superiority of Residual CNN
     
    Initial experiments with sequential models like RNNs and LSTMs revealed limitations in effectively capturing emotion-related temporal dynamics from raw EEG signals. To overcome this, a customized Residual Convolutional Neural Network (CNN) was developed. The residual blocks allowed deeper learning with reduced vanishing gradients, improving feature extraction and classification. This architecture achieved superior performance compared to 16 popular baseline models across all four emotion dimensions.
    
    Performance Highlights (DEAP dataset):
    
      Precision: 0.97
      
      Specificity: 0.96
      
      Sensitivity: 0.98
      
      F1-score: 0.97
    
      Improvement over baselines: 32.54%
  
  3. Explainability with SHAP: Identifying Key Brain Regions and Bands
  
    To ensure interpretability and reduce model complexity, SHapley Additive exPlanations (SHAP) was used to evaluate the contribution of each input feature (electrode-band pair). The SHAP analysis revealed that only a subset of electrodes—particularly in the fronto-central and parieto-occipital regions—contributed significantly to emotion recognition. Additionally, Delta and High Beta bands were found to play dominant roles in encoding emotional states.
    
    Optimized Set: 25 electrodes (61 features)
    
      Performance Retention: 98.78% of full model (200 features)
      
      Reduction in Parameters: ~24%
  
  4. Insights from Physiological Signals
  
    In addition to EEG, the DEAP dataset includes several physiological signals (e.g., eye movement, facial muscle engagement, respiration). SHAP analysis revealed that non-brain signals—particularly those related to ocular activity, facial muscle tension (EMG), and respiration—offered substantial complementary information. These signals contributed most under the Delta band, which may reflect subconscious or autonomic processes linked to emotional arousal and stress response. This finding supports the idea that combining brain and peripheral physiological inputs enhances emotion decoding and aligns with existing neuroscience literature on the brain-body interaction in affective states.
  
  5. Cross-Dataset Generalization: SEED-V and AMIGO
  
      To evaluate the robustness of the optimized feature set, it was mapped onto two external datasets: SEED-V and AMIGO. Despite differences in electrode setups and target emotion labels, the mapped models retained performance very close to their full-featured counterparts.
    
      SEED-V (6 emotions): 21 mapped electrodes (52 features) achieved 96.25% similarity to full model (64 electrodes, 320 features) while reducing parameters by 35.86%.
      
      AMIGO (4 emotions): 11 mapped electrodes (32 features) achieved 98.04% similarity to full model (17 electrodes, 85 features) with a 9.79% parameter reduction.
    
      These results validate the scalability and transferability of the SHAP-based selection strategy, enabling efficient emotion recognition with minimal signal overhead across multiple datasets and contexts.

### Key Takeaways

  1. Fronto-central and parieto-occipital electrodes dominate emotional signal encoding, especially in Delta and High Beta bands.
  
  2. Non-brain physiological signals (eye, muscle, respiration) offer crucial affective cues and should not be overlooked, especially under the Delta band.
  
  3. The proposed Residual CNN combined with SHAP-based feature pruning balances performance and interpretability.
  
  4. Cross-dataset generalization demonstrates strong potential for real-world applications in neurotechnology and affective computing, such as emotion-aware brain-computer interfaces (BCIs) and personalized mental health monitoring tools. 
