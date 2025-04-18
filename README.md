# Grammar Scoring System

## Introduction:
 - A system that can be used to assign a pre-liminary socre to spoken language (English), on the MOS Liekrt scale.
 - Uses a combination of acoustic and liguistic features of the provided audio file to predict the score.
 
## Architecture Pipeline:
 - ### Pre-processing and Feature Extraction:
    This step involves extracting:
    - acoustic features like:
        - MFCC
        - CTFT
        - ZCR
        - Spectral Centroid

    - linguistic features like:
        - Prosodic Features
         - pitch
         - f0
         - hnr
         - jitter
         - shimmer

    
 - ### Training:
    Finally, we use the extracted features for training, selected based on how strong they are correlated to the final grammar score (as provided in the training dataset).
    - Used the following algorithms for training:
      - Random Forest Regressor :-
         (*As computed for the validation set (not the same as test.csv)*)
         ```
         1. MAE: 0.693
         2. MSE: 0.764
         3. Pearson Correlation: 0.7191
         ```
      - Gradient Boosting Regressor :- 
         (*As computed for the validation set (not the same as test.csv)*)
         ```
         1. MAE: 0.632
         2. MSE: 0.659
         3. Pearson Correlation: 0.748
         ```
    - Plot out the Pearson correlation between the grammar scores and the predicted grammar scores.