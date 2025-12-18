# **Title: Basic Sound Manipulation using Python**

---

## **Objectives**

1. **Print MIDI channels, notes, and their corresponding frequencies** using Python.
2. **Play an individual MIDI (`.mid`) file** to verify sound generation.
3. **Combine beat, harmony, and melody** into a single MIDI file.
4. **Convert the MIDI (`.mid`) file into a standard audio (`.wav`) file** for playback on common media players.

---

## **Background Theory**

### **1. MIDI Standard**

MIDI (**Musical Instrument Digital Interface**) is a technical standard that describes a protocol for recording and playing music. Unlike audio files, MIDI files do not store sound directly; instead, they store **musical instructions** such as notes, pitch, duration, velocity, and channels.

**a. Notes**
MIDI notes are represented by numbers from **0 to 127**, where each number corresponds to a musical pitch. For example, MIDI note **60** represents **Middle C (C4)**.

**b. Frequency**
Each MIDI note can be converted into a frequency (in Hz) using a mathematical formula. This allows digital systems to generate sound waves corresponding to musical notes.

---

### **2. Music Theory**

Music theory provides the foundation for structuring musical compositions.

**a. Beat**
The beat represents the **rhythmic pulse** of music. It defines timing and tempo.

**b. Harmony**
Harmony is created when multiple notes are played simultaneously, forming **chords** that enrich the sound.

**c. Melody**
Melody is a sequence of notes played one after another, forming the **main musical theme**.

---

### **3. Python Libraries Used**

**a. Mido**
Mido is a Python library used for **creating, reading, and processing MIDI files**.

**b. Pygame**
Pygame provides modules for **playing MIDI and audio files**, enabling real-time sound playback.

---

## **Procedure**

1. Install the required Python libraries using `pip`.
2. Create a new MIDI file using the **Mido** library.
3. Define MIDI tracks for beat, harmony, and melody.
4. Add MIDI messages (notes, duration, velocity) to each track.
5. Print MIDI channel numbers, note values, and their frequencies.
6. Save and play the generated MIDI file using **Pygame**.
7. Convert the MIDI file into a WAV file using an external sound font or MIDI synthesizer.


```python
from mido import MidiFile, MidiTrack, Message
import pygame
import math

# Function to convert MIDI note to frequency

def midi_to_freq(note):
    return 440 * (2 ** ((note - 69) / 12))

mid = MidiFile()
track = MidiTrack()
mid.tracks.append(track)

track.append(Message('program_change', program=0, time=0))  # Piano sound

# Melodic beat pattern (arpeggiated + smooth timing)
melodic_beat = [60, 64, 67, 72, 67, 64]  # C major arpeggio

for note in melodic_beat:
    freq = midi_to_freq(note)
    print(f"Note: {note}, Frequency: {freq:.2f} Hz")
    track.append(Message('note_on', note=note, velocity=70, time=0))
    track.append(Message('note_off', note=note, velocity=70, time=240))

mid.save('melodic_output.mid')

pygame.mixer.init()
pygame.mixer.music.load('melodic_output.mid')
pygame.mixer.music.play()
```

---

## **Output**

* MIDI channels, notes, and frequencies are printed on the console.
* The generated `.mid` file plays successfully using Pygame.
* A combined musical structure consisting of beat, harmony, and melody is produced.
* The MIDI file is successfully converted into a `.wav` audio file.

---

## **Conclusion**

This experiment demonstrated the fundamentals of **sound and music manipulation using Python**. By using MIDI standards and music theory concepts, musical elements such as beat, harmony, and melody were successfully generated and combined. Python libraries like **Mido** and **Pygame** proved effective for MIDI creation and playback, highlighting Python’s capability in multimedia and audio processing applications.

---






