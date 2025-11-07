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

# 3. Verify the MFA installation
mfa --help

# 4. Install PyTorch (CPU version)
conda install pytorch torchvision torchaudio cpuonly -c pytorch

# 5. Install SpeechBrain
pip install speechbrain
```


2. 🚀 Model Preparation 
   
Pre-trained models were downloaded for English alignment.

```
# 1. Download the pre-trained English acoustic model
mfa model download acoustic english_us_arpa

# 2. Download the pre-trained English dictionary
mfa model download dictionary english_us_arpa
```

📂 Data Preparation & Validation

Data Preparation

The provided .zip file (containing .wav and .txt files) was unzipped and organized into a corpus directory at ~/mfa_data/my_corpus. The original .txt files were used directly.

Directory Structure:

Validation
The prepared corpus was validated against the dictionary to check for any errors, such as out-of-vocabulary words.
```
# Run the validation command
mfa validate ~/mfa_data/my_corpus english_us_arpa
```


4. Running the Alignment
   
The final alignment was run using the prepared corpus, the downloaded dictionary, and the downloaded acoustic model.
```
# Run the main alignment command
mfa align ~/mfa_data/my_corpus \
          english_us_arpa \
          english_us_arpa \
          ~/mfa_data/my_corpus_aligned
```

5. 📈 Outputs & Analysis
   
The resulting .TextGrid files are located in the output directory ~/mfa_data/my_corpus_aligned.
These files contain the time-aligned boundaries for every word and phoneme. They were inspected using Praat to verify the alignment quality. A full analysis, including visualizations of good and bad alignments, is available in the report.pdf.
