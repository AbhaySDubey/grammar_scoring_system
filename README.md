# Grammar Scoring System

## Introduction:
 - A system that can be used to assign a pre-liminary socre to spoken language (English), on the MOS Liekrt scale.
 - Uses a combination of acoustic and liguistic features of the provided audio file to predict the score.
 
## Architecture Pipeline:
 - ### Pre-processing:
    The pre-processing step involves:
    - clearing out noise, if any (from pre-liminary tests, I found out that it also removes fillers (such as *uh...*, *um...*, etc. out of the audio.)) - ***Not recommended***
    - trimming out leading or trailing silence (where no valid intonations can be inferred) from the audio.
    - finding out the duration of the audio and the language spoken (if not English, we stop here itself.)
    - transcribing the text (using ASR like Whisper(base/medium))

 - ### Extracting Features:
    This step involves extracting:
    - acoustic features like:
        - MFCC
        - CTFT
        - ZCR
        - Spectral Centroid

    - linguistic features like:
        - transcription length
        - Grammatical Errors (such as noun v/s verb counts, use of verb tenses, articles(a/an/the) used, prepositions used, etc.)
        - Prosodic Features

    **I'll be forming a relationship map of what features have the strongest relationship with the grammar score, based on which the features with the strongest correlation will be selected for training.**
    
 - ### Training:
    Finally, we use the extracted features for training, selected based on how strong they are correlated to the final grammar score (as provided in the training dataset).
    - I'd use a Random Forest Regressor for training. - *TBD, can use some other algorithm, too. First, I'll need to test different algorithms and their corresponding performance.*
    - Plot out the Pearson correlation between the grammar scores and the predicted grammar scores.