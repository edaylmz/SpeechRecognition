# MFCC Speech Recognition Tool
This project is built for **Assignment 2: Data Capture and Feature Computation**. It allows you to record spoken digits, extract MFCC features, and visualize them using a GUI. The system includes endpoint detection, log-mel spectral analysis, and optional noise addition.

# Assignment Requirements & Implementation

Requirement                                                                  | Implemented In                                        |
|----------------------------------------------------------------------------|--------------------------------------------------------|
| 16kHz sampling rate                                                        | `config.py` → `SAMPLING_RATE = 16000`                  |
| 16-bit PCM audio                                                           | `recorder.py` → `pyaudio.paInt16`                      |
| Automatic endpoint detection                                               | `recorder.py` → Amplitude + Zero-Crossing Rate logic   |
| Compute **log spectra**                                                    | `mfcc.py` → `power_to_db(mel_spectrogram)`             |
| Compute **cepstra** (MFCCs)                                                | `mfcc.py` → `librosa.feature.mfcc(...)`                |
| Use **40 Mel filters**, 50Hz–7000Hz                                        | `mfcc.py` → `n_mels=40, fmin=50, fmax=7000`            |
| Use **first 13 DCT coefficients (MFCC)**                                   | `mfcc.py` → `n_mfcc=13`                                |
| Compare different filter settings (40, 30, 25)                             | `main.py` and GUI dropdown                             |
| Visualize both spectrally (log-mel) and cepstrally (MFCC)                  | `plot.py`, and GUI embedded plots                      |
| Record data with noise                                                     | `utils.py → add_noise()`, GUI checkbox                 |
| Show degradation patterns under noise                                      | GUI visualization with/without noise                   |
| UI for controlling the workflow                                            | `interface.py` with Tkinter                            |
| Export MFCCs as `.csv` for analysis                                        | `interface.py` → `pandas.DataFrame.to_csv()`           |
| Replay the last recorded audio                                             | `interface.py` with `simpleaudio`                      |

---
# Code Requirements
pip install -r requirements.txt

## How the Code Runs

1. Launch the app:
   python main.py

2. The GUI will open:
  Select a digit (e.g., “zero”)
  Choose number of Mel filters (40 / 30 / 25)
  Optional: Check the Apply Background Noise box
  Press Record & Analyze

3. The system:
  Records your voice with endpoint detection
  Computes log-mel spectrogram and 13 MFCCs
  Shows them in the GUI
  Saves the MFCCs as .csv in /recordings  
  Allows replay of the latest audio

