# classifying_time_signature_in_music



## About

### Files

#### Notebooks
- collecting_data
Retrieving necessary metadata for the "small" fma audio samples, and collecting time signature from Spotify.
- data_preparation_feature_engineering
Navigating paths to audio samples and transforming into features, then structuring dataframe for models.
- Modelling



#### Csv files
- clean_track_info.csv 
    track_fma_id,
    track_spot_id,
    time_signature,
    time_sig_confidence,
    tracks_id,
    track_name,
    artist_name,
    album_name,
    track_bit,
    track_top_genre
- final_df.csv
    track_id
    mfcc features
    target variable


### Goal etc..
 
--With the advent of neural nets, the idea that a computer has the ability to find patterns within data hasn't been proven more. Through the --use of many convulutional layers, deep learning unlocks puzzles which are too complex for us humans.

The goal of this project is to use machine learning to find temporal patterns in music which give it its structure in time, namely, the time signature. --We are all familiar with the natural impulse of tapping along while vibing to a good song, --

“The aim of a beat tracker is to recover a sequence of time instants from a musical input that are consistent with the times when a human might tap their foot. Beyond an exercise in modelling a human response to a musical stimulus, beat tracking can be used in many applications including musical interaction systems, content-based audio effects, and increasingly as a meaningful temporal segmentation for higher level MIR tasks such as chord extraction, structural segmentation of audio  and music similarity.” 








### Some fundamental terminology

Fourier transform
A few buckets of paint were spilled together and we have a unique blend of colors the fourier transform can be though of the formula which 
extracts the components of which this unique blend is comrprised of.

--Mel is a transformation to have the data similar to how humans hear it.

Mel Frequency Cepstral Coefficient
"Because the discrete Fourier transform separates its input into components that contribute at discrete frequencies, it has a great number of applications in digital signal processing, e.g., for filtering, and in this context the discretized input to the transform is customarily referred to as a signal, which exists in the time domain. The output is called a spectrum or transform and exists in the frequency domain."

## Data 

### collection (and usage)

For the actual audio samples I downloaded 8000 30 second clips from https://os.unil.cloud.switch.ch/fma/fma_small.zip. The metadata for those files can be found at https://os.unil.cloud.switch.ch/fma/fma_metadata.zip. <br>
I then used Spotify's API to search up these songs by three conditions, track name, artist name, and album name. I used https://pypi.org/project/fuzzywuzzy/ to confirm that the search results were a match at over 66%. Out of 8000 samples I got accurate search results for 1419 of them. I then successfully collected the time signature for 1222 samples. After cleaning, my final dataset consisted of 
- 1034 in 4/4 time
- 128 in 3/4 time
- 42 in 5/4 time.



### Exploring

### Feature Engineering

For audio features I used Librosa to transform each sample into 20 Mel Frequency Cepstral Coefficients (MFCC).
I then took the mean for each coefficient vector for the length of sample and formed a DataFrame with the target variable being a class in time signature. 



#### Exlplaining MFCC etc..





## Modeling

Baseline model scores an accuracy of 85% always classifying the majority class of 4/4 time.
Since I had a significant class imbalance I made use of SMOTE to upsample the two remaining classes of 3/4 and 5/4 time.


### what?





## Permissions & Licenses



Audio files from FMA https://os.unil.cloud.switch.ch/fma/fma_small.zip
@inproceedings{fma_dataset,
  title = {{FMA}: A Dataset for Music Analysis},
  author = {Defferrard, Micha\"el and Benzi, Kirell and Vandergheynst, Pierre and Bresson, Xavier},
  booktitle = {18th International Society for Music Information Retrieval Conference (ISMIR)},
  year = {2017},
  archiveprefix = {arXiv},
  eprint = {1612.01840},
  url = {https://arxiv.org/abs/1612.01840},}

Thank you