# G08-ai-and-applications-project
Repository for AI and Applications course project

*Task 1: Update your tech blog using the contents from the previous group assignment. At the top of your 
blog, you should have a table of contents (I will give a slightly different instruction for those groups doing 
LG projects. I will explain more in class). The recommended format is the following:

Title of your project: Speaker-Adaptive Voice Assistant for Multi-User Homes

Members: 
Kun Lee, Dept. of Information Systems Hanyang University, ceh1502@hanyang.ac.kr
Jinseo Hong, Dept. of Information Systems Hanyang University, h0dduck@hanyang.ac.kr
Patrick Segedi, Dept. of Computer Science Chalmers Unviersity of segedi@chalmers.se

I. Introduction
- Motivation: Why are you doing this?
Our team embarked on this project with two primary motivations. 
First, we wanted to gain hands-on experience applying cutting-edge 
AI technologies to solve real-world problems. Voice recognition 
and speaker verification represent some of the most exciting 
frontiers in artificial intelligence, and we saw this as an 
invaluable opportunity to deepen our understanding of these 
technologies beyond theoretical knowledge.

Second, this project brought together students from three different 
universities across three countries - Hanyang University (Korea), 
Chalmers University of Technology (Sweden), and Zurich University 
of Applied Sciences (Switzerland). This international collaboration 
allowed us to experience diverse perspectives, work across time zones, 
and develop the communication skills essential for global tech careers.

- What do you want to see at the end?
Our ultimate goal is to see our voice assistant actually working - 
responding to real voices, recognizing different family members, 
and controlling smart home devices accordingly. We want to demonstrate 
that a privacy-preserving, speaker-adaptive voice assistant is not 
just a theoretical concept, but a functional system that can enhance 
daily life in multi-user households.

II. Datasets

Our project uses three categories of datasets:
1. pretrained public datasets used by underlying AI models,
2. user-generated enrollment voice data, and
3. real-time audio streams captured by in-home devices.
These datasets support speaker verification, speech recognition, and contextual inference. 

a) Pretrained Speaker Verification Dataset (VoxCeleb)
The ECAPA-TDNN model from SpeechBrain, used for speaker identification, is pretrained on the VoxCeleb1/2 dataset, a large-scale speaker recognition corpus containing thousands of speakers recorded in unconstrained, real-world environments.

•	Purpose in our system: extracting robust speaker embeddings for multi-user identity recognition.
We do not retrain the model but rely on the pretrained embeddings to authenticate speakers locally on the device.

b) Pretrained ASR Dataset (Whisper / Faster-Whisper)
Our wake-word detection and speech-to-text pipeline uses Faster-Whisper, an optimized implementation of OpenAI’s Whisper model. Whisper is trained on:

•	680,000 hours of multilingual speech

•	Noisy, real-world audio data

•	Diverse accents, environments, and speaking styles
This makes it suitable for household environments where commands may vary in tone or clarity.

c) User Enrollment Voice Dataset (Locally Stored)
To enable personalization and role-based access control, each household member records a set of enrollment samples during profile setup.

•	Format: WAV, 16 kHz, mono

•	Typical length: 3–5 seconds per sample

•	Number of samples: 3–5 recordings per user

•	Storage: encrypted local SQLite database

•	Purpose:

o	create user-specific embeddings

o	authenticate speakers in real-time

o	maintain privacy by preventing cloud transmission
All data remains fully on-device to ensure privacy.

d) Real-Time Environmental Audio Stream
For wake-word detection, command processing, and location awareness, the system processes continuous audio input from multiple room speakers/microphones.
•	Purpose:

o	detect speaker location

o	identify the active user

o	resolve multi-user command conflicts
Since this stream is processed on-device and never uploaded, it is considered an operational dataset rather than a stored one.

III. Methodology 

Faster-Whisper:
OpenAI’s speech-to-text model in an optimized CTranslate2 implementation. Used to convert user speech into text for wake-word detection and command processing.

SpeechBrain (ECAPA-TDNN):
Used for speaker verification. The ECAPA-TDNN model generates speaker embeddings to compare prerecorded samples with user speech.

Cosine Similarity Scoring:
Similarity between voice embeddings is computed using cosine similarity to identify the best-matching speaker.

Wake-Word Detection (Keyword-based):
A lightweight text-based wake-word detector checks whether the transcribed text contains the activation word (“Hello”).

XTTS-v2 (Coqui TTS):
A neural TTS model used to generate spoken responses with selected speaker voices.

Audio Capture (SoundDevice + WAVIO):
Used to record raw microphone audio (16 kHz mono WAV format) as input for STT and verification.

Lovelace UI:
Home Assistant’s dashboard system, used to visualize interactions with IoT devices.


IV. Evaluation & Analysis
- Graphs, tables, any statistics (if any)

V. Related Work (e.g., existing studies)
none

VI. Conclusion: Discussion
Coordinating schedules was still difficult due to different class times and personal commitments. 
We initially believed that adopting Agile with frequent meetings would 
improve efficiency, but we learned that meeting more often does not 
necessarily lead to better productivity—what mattered more was the 
quality of communication and clear task ownership between meetings.
