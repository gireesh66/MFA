# Forced Alignment with MFA

## 1. ⚙ Installation & Setup

This project was run on *Windows*.

### Anaconda Installation

First, install the *Anaconda* distribution, which includes Conda.
* *Download here:* **[https://www.anaconda.com/download](https://www.anaconda.com/download)**

### Environment Setup

Once Anaconda is installed, open the *Anaconda Prompt* and run the following commands to set up the environment.

*Installation Commands:*

```bash
# 1. Create the environment and install MFA
# (This creates an environment named "aligner")
conda create -n aligner montreal-forced-aligner

# 2. Activate the newly created environment
conda activate aligner

# 3. Install PyTorch (CPU version)
conda install pytorch torchvision torchaudio cpuonly -c pytorch

# 4. Install SpeechBrain
pip install speechbrain

# 5. Verify the MFA installation
mfa --help
```


# 2.🚀 Model Preparation
   
Pre-trained models were downloaded for English alignment.

**Download the pre-trained English acoustic model**
```
mfa model download acoustic english_us_arpa
```
**Download the pre-trained English dictionary**
```
mfa model download dictionary english_us_arpa
```

# 3.📂 Data Preparation & Validation

**Data Preparation**

The provided .zip file (containing .wav and .txt files) was unzipped and organized into a corpus directory at ~/mfa_data/my_corpus. The original .txt files were used directly.


The data was structured into a multi-speaker format, with *two speaker directories* (speaker1 and speaker2), each containing 6 audio files and their 6 corresponding transcription files

the folder structure as compatible with MFA

**Directory Structure:**
```
mfa_data/my_corpus/
├── speaker1/
│   ├── audio_001.wav
│   ├── audio_001.txt
│   ├── audio_002.wav
│   ├── audio_002.txt
│   ├── audio_003.wav
│   ├── audio_003.txt
│   ├── audio_004.wav
│   ├── audio_004.txt
│   ├── audio_005.wav
│   ├── audio_005.txt
│   ├── audio_006.wav
│   ├── audio_006.txt
│
└── speaker2/
    ├── audio_001.wav
    ├── audio_001.txt
    ├── audio_002.wav
    ├── audio_002.txt
    ├── audio_003.wav
    ├── audio_003.txt
    ├── audio_004.wav
    ├── audio_004.txt
    ├── audio_005.wav
    ├── audio_005.txt
    ├── audio_006.wav
    ├── audio_006.txt
```

**Validation**
The prepared corpus was validated against the dictionary to check for any errors, such as out-of-vocabulary words.

**Run the validation command**
```

mfa validate ~/mfa_data/my_corpus english_us_arpa
```


# 4. Running the Alignment
   
The final alignment was run using the prepared corpus, the downloaded dictionary, and the downloaded acoustic model.

**Run the main alignment command**

```
mfa align ~/mfa_data/my_corpus english_us_arpa english_us_arpa ~/mfa_data/my_corpus_aligned
```
# 5. 📈 Outputs & Analysis
   
The resulting .TextGrid files are located in the output directory ~/mfa_data/my_corpus_aligned.
These files contain the time-aligned boundaries for every word and phoneme. They were inspected using Praat to verify the alignment quality. A full analysis, including visualizations of good and bad alignments, is available in the report.pdf.
