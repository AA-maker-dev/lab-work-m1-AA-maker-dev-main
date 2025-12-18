# Title: **Basic Sound Manipulation using Python**

##  **Objectives**

1. **Load and play** a sample audio file (`drum.wav`)
2. **Process and manipulate** audio signals
3. **Synthesize** audio/soundwaves from scratch
4. **Visualize** audio waveforms and spectral properties

---

#  **Background Theory**

---

#  **1. Sound and Audio Representation**

Sound is a **mechanical wave** created by vibrations in the environment. These vibrations produce **continuous analog signals** whose amplitude and frequency vary smoothly over time.

Since computers cannot process analog signals directly, the sound must be converted into **digital form**. Digital audio consists of **samples**, numerical values representing the amplitude of the sound wave at discrete moments in time.

###  **Key Terms**

| Term               | Meaning                       |
| ------------------ | ----------------------------- |
| **Frequency (Hz)** | Vibrations per second (pitch) |
| **Amplitude**      | Loudness or signal strength   |
| **Waveform**       | Shape of the signal           |
| **Channels**       | Mono, stereo, surround        |

---

#  **2. Sampling and Quantization**

These two processes form the backbone of **Analog-to-Digital Conversion (ADC)**.

---

##  **A. Sampling**

Sampling is the process of measuring the amplitude of the sound at **equally spaced time intervals**.

```
Analog Signal (Continuous Wave)
   
   /\/\/\/\/\/\/\/\/\/\  
      |   |   |   |     
      S1  S2  S3  S4     ← Sampling points
```

###  **Nyquist Sampling Theorem**

To reconstruct a signal properly:

> **Sampling Rate ≥ 2 × Highest Frequency**

| Audio Type | Sampling Rate |
| ---------- | ------------- |
| Telephone  | 8 kHz         |
| CD Quality | 44.1 kHz      |
| Studio     | 96 kHz        |

---

##  **B. Quantization**

Quantization converts each sampled amplitude into a **fixed number of digital levels**.

```
Amplitude Levels (Digital)
|
|     ●   ●       ●
|   ●   ●   ●   ●  
| ●               ●
+--------------------> Time
```

###  **Bit Depth Levels**

| Bit Depth | Levels      |
| --------- | ----------- |
| 8-bit     | 256         |
| 16-bit    | 65,536      |
| 24-bit    | 16 million+ |

Higher bit depth = **lower noise + higher accuracy**.

---

#  **3. PyDub – Background Theory**

PyDub is a **high-level audio editing** library in Python.
It uses **FFmpeg** internally for decoding and encoding.

###  **What PyDub Can Do**

* Load audio (MP3, WAV, FLAC, etc.)
* Slice/trim audio
* Increase/decrease volume
* Add effects (fade-in/out)
* Merge multiple audio files
* Convert formats
* Export audio

###  **PyDub Example**

```python
from pydub import AudioSegment

# Load audio file
audio = AudioSegment.from_file("music.mp3")

# Cut first 5 seconds
cut_audio = audio[:5000]

# Increase volume by +6 dB
louder = cut_audio + 6

# Fade in and fade out
processed = louder.fade_in(2000).fade_out(2000)

# Export result
processed.export("output.wav", format="wav")
```

---

#  **4. Librosa – Background Theory**

Librosa is a **powerful audio analysis and feature extraction library** widely used in:

* Machine learning
* Music information retrieval
* Signal processing
* Speech recognition

###  **Key Features**

* Load audio as numerical arrays
* Waveform visualization
* Spectrogram & Mel-spectrogram
* MFCC extraction
* Pitch detection
* Beat tracking
* Audio transformations

###  **Librosa Example**

```python
import librosa
import librosa.display
import matplotlib.pyplot as plt

# Load audio
y, sr = librosa.load("music.wav")

# Plot waveform
plt.figure()
librosa.display.waveshow(y, sr=sr)
plt.title("Waveform")
plt.show()

# Extract MFCC features
mfccs = librosa.feature.mfcc(y=y, sr=sr, n_mfcc=13)

print("MFCC shape:", mfccs.shape)
```

---

#  **Procedure**

```
1. Install Python libraries (PyDub, Librosa, Matplotlib, NumPy)
2. Load the audio file (drum.wav)
3. Play and visualize the waveform
4. Edit and manipulate using PyDub:
      - Trimming
      - Fading
      - Mixing
      - Changing speed/volume
5. Use Librosa for analysis:
      - Spectrogram
      - Mel Spectrogram
      - MFCC extraction
6. Generate synthetic tones (sine wave, square wave)
7. Plot outputs (waveform, spectrum)
8. Export results
```

---

#  **Output**

* Original Audio Signal
<img width="1267" height="247" alt="image" src="https://github.com/user-attachments/assets/2cc3771c-a86f-43dd-a546-8ee2e06f9a17" />

* Sampled Audio Signal
<img width="600" height="174" alt="image" src="https://github.com/user-attachments/assets/b748b22c-70f9-4014-adb5-754a02f00f3d" />

* Quantized Audio Signal
<img width="630" height="196" alt="image" src="https://github.com/user-attachments/assets/eec75347-f53b-4455-9e8a-35bd88e744f7" />

---

#  **Conclusion**

This experiment demonstrates how Python can be used for **audio manipulation, editing, synthesis, and visualization**. Using libraries such as **PyDub** and **Librosa**, it is possible to load sounds, process them, analyze their spectral properties, and even generate new audio signals from scratch. These tools are essential for applications in music technology, machine learning, and digital audio processing.

---
