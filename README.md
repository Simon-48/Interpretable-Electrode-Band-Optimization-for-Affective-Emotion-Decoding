# Interpretability-Driven-Optimization-of-EEG-Electrode-Selection-for-Emotion-Analysis

This project aims to perform emotion recognition using the DEAP dataset, which contains EEG recordings from 32 participants using 40 electrodes. The objective is to predict four emotional dimensions: arousal (intensity of emotion or alertness), valence (pleasantness of the emotion), dominance (control or influence over the emotion), and liking (subjective preference or enjoyment).

Initially, the Fast Fourier Transform (FFT) was applied to convert the raw EEG signals from the time domain to the frequency domain. This transformation allowed the data to be structured in a tabular format with five frequency bands per electrode, making it suitable for conventional modeling techniques.

It is important to note that sequential models like LSTM and RNN did not perform significantly well on raw EEG time-series data. Later, a customized Convolutional Neural Network (CNN) was developed. This CNN outperformed other deep learning and traditional machine learning models in terms of accuracy and robustness.

The models were first trained using all 40 electrodes. To enhance interpretability and reduce computational overhead, SHAP (Shapley Additive exPlanations) analysis was used to identify the most important electrodes and their respective frequency bands. Interestingly, the proposed CNN model trained with only this optimized set of electrodes and bands achieved nearly the same performance as the full model while drastically reducing computational time and model complexity.

**The notebook EEG_Conversion contains the conversion of raw EEG data from the time domain to the frequency domain. The Brain_models notebook includes the implementation of various models trained on the full dataset for binary classification.**

**The notebook Brain-XAI-Updated contains the ideal set of electrodes. Based on this, the optimal electrodes were utilized in the IDEAL_EEG notebook for binary classification tasks and in the IDEAL_EEG_Multiclass notebook for multiclass prediction tasks. All the above analyses are done based on person-dependent data, where the data is separated based on videos rather than individuals. Therefore, the same person's data may appear in both the training and testing sets, differentiated by the videos.** 

**Additionally, in the Models_PersonIndependent notebook for binary classification and the PersonIndependent_IDEAL_EEG_Multiclass notebook for multiclass classification, the optimal set of electrodes is used for person-independent analysis, where the training and testing data consist of a mixture of data from different individuals. The conversion for person-independent analysis is provided in the EEG_PersonIndependent notebook.** 
