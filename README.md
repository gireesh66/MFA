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
