# classifying_time_signature_in_music



## About

### Goal
 
We are all familiar with the impulse of tapping along while vibing to a good song. For a given song, these beats are organized in groups allowing the song to have its structure. This structure is called 'Time signature'. It's commmon for a pop song to be in 4/4 time and for a waltz to have a time signature of 3/4. <br>

<img src="time-signature.png" />

The goal of this project is to use machine learning to classify an audio sample's time signature by finding temporal patterns. Beyond an exercise in modelling a human response to a musical stimulus, this can be useful for a dj who wants to filter songs by the way we dance to it, or for music interaction systems which can search through a library of beats and apply a match for a given audio sample. 


### Files

#### Notebooks
- collecting_data
Retrieving necessary metadata for the "small" fma audio samples, and collecting time signature from Spotify.
- data_preparation_feature_engineering
Navigating paths to audio samples and transforming into features, then structuring dataframe for models.
- Modelling



#### Csv files
- clean_track_info.csv 
    <br>track_fma_id,
    <br>track_spot_id,
    <br>time_signature,
    <br>time_sig_confidence,
    <br>tracks_id,
    <br>track_name,
    <br>artist_name,
    <br>album_name,
    <br>track_bit,
    <br>track_top_genre
- final_df.csv
    <br>track_id
    <br>mfcc features
    <br>target variable







## Data 

### collection (and usage)

For the actual audio samples I downloaded 8000 30 second clips from https://os.unil.cloud.switch.ch/fma/fma_small.zip. The metadata for those files can be found at https://os.unil.cloud.switch.ch/fma/fma_metadata.zip. <br>
I then used Spotify's API to search up these songs by three conditions, track name, artist name, and album name. I used https://pypi.org/project/fuzzywuzzy/ to confirm that the search results were a match at over 66%. Out of 8000 samples I got accurate search results for 1419 of them. I then successfully collected the time signature for 1222 samples. After cleaning, my final dataset consisted of 
- 1034 in 4/4 time
- 128 in 3/4 time
- 42 in 5/4 time.

---ADD visual of classes for top genre

### Exploring

### Feature Engineering

For audio features I used Librosa to transform each sample into 20 Mel Frequency Cepstral Coefficients (MFCC).
I then took the mean for each coefficient vector for the length of sample and formed a DataFrame with the target variable being a class in time signature. 


#### Exlplaining MFCC etc..

----Add visual of how it looks

### Some fundamental terminology

Fourier transform
A few buckets of paint were spilled together and we have a unique blend of colors the fourier transform can be though of the formula which 
extracts the components of which this unique blend is comrprised of.

--Mel is a transformation to have the data similar to how humans hear it.

Mel Frequency Cepstral Coefficient
"Because the discrete Fourier transform separates its input into components that contribute at discrete frequencies, it has a great number of applications in digital signal processing, e.g., for filtering, and in this context the discretized input to the transform is customarily referred to as a signal, which exists in the time domain. The output is called a spectrum or transform and exists in the frequency domain."



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