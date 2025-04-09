# Interpretability-Driven-Optimization-of-EEG-Electrode-Selection-for-Emotion-Analysis

This project aims to perform emotion recognition using the DEAP dataset, which contains EEG recordings from 32 participants using 40 electrodes. The objective is to predict four emotional dimensions: arousal (intensity of emotion or alertness), valence (pleasantness of the emotion), dominance (control or influence over the emotion), and liking (subjective preference or enjoyment).

Initially, Fast Fourier Transform (FFT) was applied to convert the raw EEG signals from the time domain to the frequency domain. This transformation allowed the data to be structured in a tabular format with five frequency bands per electrode, making it suitable for conventional modeling techniques.

Point to be noted that since sequential models like LSTM and RNN did not perform significantly well on raw EEG time-series data. Later, a customized Convolutional Neural Network (CNN) was developed. This CNN outperformed other deep learning and traditional machine learning models in terms of accuracy and robustness.

The models were first trained using all 40 electrodes. To enhance interpretability and reduce computational overhead, SHAP (SHapley Additive exPlanations) analysis was used to identify the most important electrodes and their respective frequency bands. Interestingly, the proposed CNN model trained with only this optimized set of electrodes and bands achieved nearly the same performance as the full model, while drastically reducing computational time and model complexity.
