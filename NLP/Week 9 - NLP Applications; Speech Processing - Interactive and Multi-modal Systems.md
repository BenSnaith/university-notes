### Definitions of Speech Processing Tasks

 - Automatic Speech Recognition (ASR) / Speech-to-Text (STT) / Transcription
	 - Translating Audio input (waveform) to text output (characters, tokens, words, sentences).
 - Streaming ASR
	 - Transcribing continuous audio, e.g., captions, dictation. Contrast with transcribing whole text once received.
 - Large-Vocabulary ASR (LV-ASR)
	 - Historical term for general ASR, since recognition of a limited vocabulary such as digits of voice commands was easier, and all that was feasible.
 - Conversational Speech Recognition (CSR)
	 - Newer term: ASR in the context of dialogue, including management of turn-taking, interruptions, agreements, etc.
 - Speech Synthesis / Text-to-Speech (TTS)
	 - Translating text input (words, sentences) to audio output.
 - Speech Language Models (SLM)
	 - Emerging class of models to translate speech directly to speech, not via text.

### Challenges for Speech-to-Text

![[Pasted image 20251202165559.png]]
![[Pasted image 20251202165615.png]]

### State of the Art

Automatic Speech Recognition is usually measured by Word Error Rate (WER)

![[Pasted image 20251202165653.png]]

Difficult to compare results because the difficulty of the task varies. Standard benchmarks exist, e.g., [1, 2]:

![[Pasted image 20251202165733.png]]

Automatic Speech Recognition has always been dependent on:

Data (high quality) <-> Computational Power <-> Advanced Processing Algorithms

As text-based NLP, but more so, due to the **complexity of the signal** (and therefore *high sampling rate*).

ASR becoming (very recently) mainstream therefore largely due to:

 - **Data**: availability of vast amount of data, particularly paired audio-text (transcription) on the internet.
 - **Computation Power**: Advances in GPU's, TPU's.
 - **Advanced Processing Algorithms (Deep Learning)**: able to manage and make use of the data for training and inference, manage multiple GPUs in parallel, use lower-quality data.

Plus commercial drivers.

### Speech Production - Source-filter model

Basis of human communication.

Produced audio as sound pressure wave, shaped by the human vocal tract as it changes shape (e.g., movement of tongue and lips) and introduces constructions (placement of tongue, lips, etc.)

Often modelled as a sound-producing source (the vocal folds) and filter (shape of the vocal tract).

Early **speech synthesizers** consisted of just that: a reed to generate sound, plus some tubes to simulate the vocal tract and modulate the sound (plus bellows the model of the lungs).

![[Pasted image 20251202170815.png]]

### Production - Vowels

`/iy/`

These represent *phonemes*, the specific speech sounds in a language.

The notation is ARPAbet. This representation is more precise than typical spelling, e.g.

seal -> /s/ /iy/ /l/
wheel -> /w/ /iy/ /l/

There are around 45 phonemes in the English language, depending on the system used (some sounds can be further divided, such as /d/ into a closure (silence) plus a burst (try it), and a diphthong vowel which changes over its duration). Other languages may have more, or fewer.

The basic problem is ASR is to map audio to phonemes, and then to words, sentences, etc.

Nowadays, phonemes are often bypasses in favour of modelling characters directly, but the basic principle of mapping to unique speech sounds remains.

### Fourier Transform

Any speech signal can be decomposed to a sum of sine or cosine waves.

To convert a signal $x_n$ in the time domain to $X_k$ in the frequency domain use the (fast) Discrete Fourier Transform:

![[Pasted image 20251202171556.png]]

"To find the energy at a particular frequency, spin your signal around a circle (find the period / repeats of the sine / cosine wave) at that frequency, and average a bunch of points along that path".

![[Pasted image 20251202171543.png]]

### Perception

![[Pasted image 20251202171623.png]]

### Summary - Human Speech

Speech is produced by air passing though the *vocal folds* and transformed by the *vocal tract* (including the trachea mouth and nasal cavities). The varting shape of these causes *resonant frequencies* particularly noticeable in *vowels*.

Sounds are further shaped by *constructions* including the position of the *tongue, teeth* and *palate*, creating consonants such as *plosives* (b, t, d, g, k, p), *fricatives* (s, sh, j, jh), etc.

Speech is often modelled using the *source-filter* mode. This has been used to create simple (pre-machine-learning) speech synthesizers.

Speech is transmitted to the hearer through the air as *sound pressure waves*.

The *Fourier transform* can be used to convert this frequency representation, which allows extraction characteristic features useful for ASR.

### Automatic Speech Recognition

![[Pasted image 20251202172054.png]]
![[Pasted image 20251202172106.png]]
![[Pasted image 20251202172120.png]]

### Feature Extraction to MFCCs

![[Pasted image 20251202172356.png]]

### Summary - Feature Extraction

Feature extraction for all types of speech processing (ASR, speech synthesis, speaker identification, ...) has historically been based on Fourier transforms to convert from the temporal to frequency domain, followed by the transformation to *log mel filterbanks* and *mel-frequency cepstral coefficients (MFCCs)*. The latter are closely related to how humans produce and perceive speech, because that is reflected in the features on the signal.

The speech waveform can be considered as a *sum of sine or cosine waves*; hence the Fourier transform is able to extract the underlying frequencies.

Speech is digitised at a specific *sampling frequency* and stored at a specific *bit rate*. The sampling frequency limits the resolution in the time domain (the *Nyquist frequency* is the highest frequency that can be identified by the Fourier transform: half the sampling frequency). The *bit rate* limits the resolution in the amplitude domain.

Deep learning has enabled high-level features to be learned directly from data, using self-supervised learning models such as Wav2Vec 2.0, WavLM and HuBERT: these are covered later.

### Automatic Speech Recognition

![[Pasted image 20251202173204.png]]

### A brief history of ASR

1940s - 1980s: Template matching

1980s - 2000s: Temporal modelling with Hidden Markov Models and acoustic modelling with Gaussian Mixture Models: HMM/GMMs

2010s: The "Deep Learning Revolution"

Mid-2010s: The "Sequence-to-Sequence Revolution" (tranducers, encoders-decoders)

Late-2010s: The "Attention Revolution" (transformers, foundation models)

Present-Day: The "Generative AI Revolution" (LLMs)

### Early ASR - Template Matching

Phone templates - acoustic pattern for each sound.

**Dynamic time warping**: account for variation in duration of sounds.

Pattern matching to best sequence of sounds.

To around 1980s, limited scope, e.g., digit recognition.

### 1980 - 2000: Hidden Markov Models (HMM)

The HMM states (1, 2, ... 6) model how a sound evolves over time, governed by the transition distribution:

One HMM per triphone e.g., /uw/ in context: "suit" -> /sh/ /iy/ /h/ (several 1000 overall).

Gaussian Mixture Model (GMM) output distributions (observations).

Viterbi alignment algorithm learns the best mapping of acoustic features to HMM states.

Decoding is via a "lattic" to determine the sequence of models that best explains the audio.

Dominant to the 2000s, requires expensive phone-labelled data.

What is this?

We know we have a sequence of sounds (e.g., phonemes, characters) that "explains" the audio, and that these occur in sequence.

We can model that as a Markov Process. The "Markov" part means that each state is only dependent on the one before.

And draw that as shown. Here each circle represents a state, meaning a speech sound.

We work from left to right. At each time step, as we observe speech features (top), we have a probabilistic choice between remaining in that state (red loop) or moving on.

BUT we have a problem: we can't observe the actual speech sounds (/sh/ etc.) -- they are "hidden". We can only the features (observations) and use them to infer the actual speech sound that produced them.

![[Pasted image 20251202174314.png]]

The **Hidden Markov Model** adds a model of output distributions at each state.

From data (pairs of audio with transcriptions) we learn which features are likely to indicate /sh/, which are likely to indicate /iy/ and so on. These are modelled as a Gaussian Mixture Model (GMM).

![[Pasted image 20251202174431.png]]

Using an iterative algorithm such as the forward-backward or Viterbi algorithms we learn from data the parameters of the transition probabilities and output probabilities (for observations) that best explain each speech sound such as /iy/.

We learn an HMM for each phoneme in context, known as a triphone (e.g., /sh/, /iy/, /h/). This is because we know that surrounding context changes the sounds.

We also have multiple states per HMM, to further acknowledge that speech sounds are not fixed by evolve over their duration, e.g., as the vocal tract moves into the right configuration, the moves towards the next sound.

The figure shows an example of /iy/ in context, the triphone /sh/, /iy/, /h/. There will be many other triphones with /iy/ at the center.

In this case we have 5 states for each triphone.

To transcribe from audio to a sequence of phones, we put all HMMs together in a lattice (all possible orders for the output phones), then find the highest probability path through the lattice -- similar to *dynamic time warping*.

In the figure, we move from left to right as speech features are processed. Each row represented a particular trained triphone HMM.

We can move between any of them, to work out multiple paths that could represend the sequence of speech sounds that best explains the audio.

The sequence / explanation with the highest probability represented the output text.

![[Pasted image 20251202180202.png]]

### The Deep Learning Revolution

![[Pasted image 20251202180235.png]]

### Summary - ASR Models

Each speech recognition was performed by **pattern-matching** explicit templates for specific sounds. This was limited to specific sounds.

*Dynamic time warping* allowed these to be modified to account for sounds produced differently of difference occasions. ASR was still limited to spoken digits 0 ..= 9.

*Hidden Markov Models* allowed statistical modelling of time sequences such as acousing features. With *Gaussian Mixture Models* of output feature distributions these enabled large-vocabulary ASR (LV-ASR). ASR was dependent on expensive hand-labelled audio transcripts (text) at a great level of detail (individual phones).

*Deep Learning / Deep Neural Networks* have allowed for rapid advance.

*Why do we care about these "old" systems?* HMMs give us a way to explain / illustrate the fundamental problems of temporal modelling an unknown (hidden) sequence based only on observations. The processing carried out by modern deep learning / sequence / transformer systems is fundamentally the same; the connections to human speech processing are just less obvious. HMMs are also still relevant when we do not have the vast amounts of transcribed (or even un-transcribed) audio data that modern systems require, such as in *low-resource* scenarios. Smaller, well-trained models can then perform better than larger, poorly-trained models.

### Recurrent Neural Networks and CTC

![[Pasted image 20251202181513.png]]

### Connectionist Temporal Classification

1. Every 10ms feature $x_i$ -> 1 character $y_i$.
2. Collapse identical characters:
   alignment: `h h h h e e e l l l l l l l l o o o o o` -> helo!
3. Add a special blank symbol `_` to the alphabet to handle silence and repeating characters
   alignment: `h h h h e e e l l l l _ l l l l o o o o` -> hello
4. Sum probabilities over all the equivalent sequences, e.g.

Most probable: `h h h h e e e l l l l l l l l o o o o o` -> helo
Next most probable: `h h h h e e e l l l _ l l l l o o o` -> hello
Next most probable: `h h h h _ e e e l l _ l l o o o o o` -> hello

-> Transcription is 'hello'.

![[Pasted image 20251202192239.png]]

CTC assumes each symbol is independent of the one before, therefore the final decode must be combined with a language model (to bias towards true word sequences) and length factor L(Y) (to avoid penalising longer sequences due to the multiplication of more probabilities):

![[Pasted image 20251202192359.png]]

### The sequence-to-sequence revolution

We met sequence-to-sequence models when we looked at machine translation.

In ASR it provides a direct solution to the problem of:

 - Mapping from a very long (acoustic feature) sequence to a much shorter (character) sequence,
 - Where we do not know exactly how the sequences map to each other.

The encoder learns a contextualised representation $h_i$ of the acoustic (speech) features $x_i$ at each step. The final hidden representation $h_n$ conveys the essence of the input to the decoder. The decoder uses this context in addition to all previous history, to generating output text.

Subsampling (compression) often uses a Convolutional Neural Network (CNN) to intelligently reduce dimension accounting for patterns in time and frequency (as the self-supervised learning feature representation models).

Training and output sequences:

`<SOS> - token sequence Y - <BOS>`
$Y$ includes characters, space, and punctuation.

CTC loss function often used to improve sequence decoding.

![[Pasted image 20251202193101.png]]

### Transformers: seq2seq with Attention

We also say the **Transformer** models and **Attention** concept in weeks 4 and 5.

**Whisper** is a **Transformer** sequence-to-sequence model (with **Attention**) that has defined the state-of-the-art for speech tasks including ASR for several years.

One of the original **Foundation Models** Whisper is a *huge model* designed for *multiple speech tasks*.

ASR is selected using a special token.

![[Pasted image 20251202193326.png]]

### Whisper

**Whisper Large v3**:

Training data:

1,000,000 hours multilingual paired audio & transcripts scraped from the internet,

4,000,000 hours pseudo-labelled audio from previous version.

Large model:

32 Transformer blocks (decoder & encoder).
1,280 dimension layers.
= 1,500 million parameters / 3.06GB

Learned sinusoidal position embeddings.

Subsample:

2 CNN layers reduce dimension to 1,500.

Input: 

30 seconds.
128 log Mel features, 25ms windows,
10ms stride = 3,000 dimension.

![[Pasted image 20251202193326.png]]

Whisper transcribes long audio by transcribing overlapping chunks, then stitching the transcriptions together.

Whisper is a large foundational model and should do reasonably well on many speech tasks including ASR. It was state-of-the-art when released and still competitive. Training or fine-tuning Whisper however will be infeasible for most users due to the vast number of parameters, and hence amount of computational power and training data needed.

Meta Omnilingual ASR has very recently been released at possibly a step-changed improvement, specially on low-resource languages where limited or no training data is available.

### Decoding

Although sequence-to-sequence models inherently model language in the decoder, the language model is often not as good as it could be, as the models are huge, and the amount of paired acoustic-text data is relatively smaller.

Therefore we often add a language model.

Multiple hypotheses are output by the acoustic model (e.g., Transformer) e.g., using Beam Search.

These are rescored by a language model and normalised or length ($Y_c$), so that longer sentences are not penalised.

![[Pasted image 20251202194236.png]]

### Self-supervised learning (SSL)

Self-supervised learning is learning patterns in data without explicit labelling - the algorithm creates its own labels.

Self-supervised learning of speech representations aims to solve two problems with ASR.

 1. Huge acoustic models perform well but only if they have enough data of good enough quality to train well: If some of the acoustic modelling can be done without labelled data, this would reduce the data dependency.
 2. There are no explicit acoustic patterns in audio, and no explicit segmentation between speech sounds: the traditional acoustic modelling is human-designed and may not be the best available: using vast data and deep neural networks we can now automatically learn (better?) representations.

Self-supervised representation learning such as HuBERT (HSU et al., 2021) and Wav2Vec 2.0 (Baevski et al., 2020) follow a similar approach to BERT for text:

 1. *Cluster* MFCC features into 100 classes: aim: learn phonetic representations.
 2. Repeat, clustering into 500 classes: aim: learn more detailed representations.
 3. Train the model to predict classes, from sequences of features, by masking some features and requiring the model to learn to predict the classes to which the feature belongs to - as for BERT.

### Self-supervised learning - HuBERT

![[Pasted image 20251202194912.png]]

### Feature extraction - Data Augmentation

Availability of data has always been a constraining factor. Early systems needed detailed hand-labelled transcriptions to the phone level. New systems can make use of sentence-transcribed data, lower quality transcriptions, and to some extent non-transcribed audio (self-supervised learning).

However models are larger, meaning more data is needed.

**Data augmentation** is one way of artificially increasing the amount of data, in an attempt to simulate in training data, a more complete coverage of the distribution of speech that the ASR system might encounter in production. Copies of the original recording are created with:

 - **Added noise** of various types (while noise, traffic, babble, ...)
 - **Time warping** create copies of the training recordings artificially sped up and slowed down.
 - **Masking the waveform** in the time and frequency domains: remove parts of the signal.
 - **Masking the spectrogram** (as an image) in the time and frequency domains.

A **standard** approach is **SpecAugment** (Park et al., 2019), which combines many of the above to increase the **amount** and **variety** of data used in training.

### Streaming (real-time) transcription

**Transformer** models with **Attention** such as **Whisper** provide state-of-the-art transcription accuracy.

But they cannot be used in a streaming (continous) mode - as seen on video stream transciption.

**Why?**

Attention needs the **entire input** to compute the **hidden state sequence** before decoding can begin.

This is why Connectionist Temporal Classification (CTC) is still state-of-the-art. CTC decodes letter by letter immediately. But, it assumes all outputs are independent - no language model or history: CTC needs an improvement to allow it to learn from history.

**Solution**: The RNN-Transducer (RNN-T): **similar to the sequence-to-sequence model**.

### Steaming: RNN-Transducer

The **RNN-Transducer (RNN-T)** combines an encoder and decoder with a **Joiner** network.

The **encoder** learns to produce a hidden representation from the acoustic features.

The **decoder** (a standard language model) learns to produce a hidden representation useful for predicting the next output token (character) $y_i$.

The **joiner network** learns to combine the hidden representations to produce an output probability distribution over all possible outputs.

![[Pasted image 20251202200222.png]]

### ASR: data and evaluation

**Data:**

Early ASR relied on **phone-level transcribed** data: very expensive to produce: small-scale data was either fully hand-labelled or semi-automatically labelled by hand-labelling a small amount of audio from which a mapping from acoustic features to labels could be learned, then using **forced-alignment** to automatically find the best phone start- and end- alignment using the hand-labelled data.

Datasets include TIMIT, Wall-Street Journal.

**Sequence-to-sequence models** learn directly from acoustic-text pairs at the sentence level.

Datasets include LibriSpeech (books read by volunteers) Mozilla CommonVoice (multi-lingual data collected by volunteers), FLEURS (multi-lingual), TED-LIUM (TED talk transcripts).

**Foundation models** such as Whisper, Google Universal Speech Model (USM) learn from vast amount of lower-quality paired audio-text transcriptions scraped from the internet, although the exact data is not made public.

**Self-supervised learning models** such as Wav2Vec 2.0, HuBERT, WavLM learn from unlabelled data. Smaller amounts of labelled data are used to train an ASR model on top of the SSL representations.

Evaluation:

Typically: Word Error Rate (WER) bsed on penalising insertions, deletions, and substitutions.

![[Pasted image 20251202201026.png]]

Character Error Rate (CER) is also used for sequence models.

Other metrics base on human perception are available, but difficult to standardise. Text must usually before evaluating, to remove the effects of punctuation, capitalisation, etc.

### Summary - ASR models

**Deep learning / Deep Neural Networks** have allowed a rapid advance, first to better model **output acoustic distributions**, then to model sequences directly (using the **Connectionist Temporal Classification** loss function over sequences), then sequence-to-sequence models, attentions / transformers, and newer models.

The availability of **vast datasets**, the ability to learn from low-quality data scraped from the internet, and self-supervised learning have further enhanced the state-of-the-art.

The older CTC model / loss function is still relevant, enabling **streaming ASR** and **ASR on small devices**

HMM / GMM approaches are still relevant, enabling ASR in low-resource scenarious. Very recent advances such as Meta's Omnilingual ASR may start to change that.

### Speech Frameworks

A big part of the challenge of working with speech is:

 - Managing vast amounts of data - in the past, this had to be carefully labelled.
 - Finding audio files and manipulating into the format required by models.
 - Mapping audio files to ground truth transcription.
 - Batching training data to pass to GPUs (maybe multiple in parallel) and retrieve results.

As models now real millions and billions of parameters, and training data into terabytes, it becomes less feasible (especially in academia) to train new models. We increasingly rely on Foundation or pre-trained models and either use them unchanged, or fine-tune (small additional training), or adaprt (e.g., using LoRA to traind additional parts of the model to modify outputs).

Now that speech processing has become relatively mainstream, several toolkits and framworks have become available. In general, these aim at abstrating away some of the complexity of managing data, models, training and results gathering.

Data and model management remains a large part of working with speech / audio.

We saw code to interact with **Whisper** earlier. Several models are similarly available for download, or access via an API. from similar sources, and commercial / paid-for APIs e.g., to Google, DeepGram or ElevenLabs.

**Deep Learning Frameworks** such as **Torch / TorchAudio** also provide models and datasets, often by integrating with **HuggingFace**. Speech-specific toolkits aim to abstract further, specifically to unify speech processing tasks.

![[Pasted image 20251202210239.png]]

### Torch / TorchAudio Example

There is a fuller (but still brief) tutorial on the lab pages on Blackboard.

We demonstrate using Torch to:

 1. Download and inspect a pre-trained Wav2Vec 2.0 ASR model and CTC decoder.
 2. Initialise the decoder.
 3. Transcribe out own audio recordings.
 4. Assess the result using WER and observing the actual errors made.
 5. Demonstrate an approach to streaming ASR.

![[Pasted image 20251202210536.png]]

### SpeechBrain Example

Here we briefly illustrate the main aspects of SpeechBrain.

See the lab for a fuller lab / tutorial as an introduction to using SpeechBrain for ASR using pre-defined models, and fine-tuning a relatively simple model on a new dataset.

SpeechBrain aims to provide a unified interface to many speech tasks, including ASR, TTS, speech enhancement, source separation, and others.

For ASR, it provides mainly:

 - **Data management**.
 - **Mark-up** files (YAML format) for **specifying all parameters** including model structure, training details.
 - The "**Brain Class**" as a template for managing data manipulation, training, transcription.
 - **Pre-trained models** and "**recipes**" for training and inference, integrated with HuggingFace.

A speech recogniser consists of code to set up and use the "**Brain Class**", and a YAML file.

### SpeechBrain - Hyperparameters

For example to specify a neural network involving CNN, RNN and DNN layers.

We include the following sections (here specified inside a Jupyter Notebook):

![[Pasted image 20251202211506.png]]

### SpeechBrain - Brain

The Brain provides methods to:

 - Obtain output probabilities (over characters or tokens) from input audio.
 - Calculate the loss for training (e.g., cross-entropy loss).
 - Carry out actions e.g., at the start or the end of a training epoch to calculate metrics.

![[Pasted image 20251202211840.png]]

### SpeechBrain - Data Preparation

A data preparation method is defined to manage a dataset.

A dataset object then comprises data plus management utilities:

![[Pasted image 20251202211933.png]]

A method will still need to be written to find relevant files - audio and transcription:

![[Pasted image 20251202212034.png]]

And collect metadata to instruct SpeechBrain where to find them for processing:

![[Pasted image 20251202212054.png]]

### SpeechBrain - Putting it all together

Finally we train the model by calling the "fit" method on the Brain, then evaluate results:

![[Pasted image 20251202212210.png]]

This will run for the number of epochs defined in the hyper-parameter file, and carry out the steps defined there, using the methods defined in the "Brain" class.

![[Pasted image 20251202212221.png]]

### Wrap-up

In this session we reviewed the fundamentals of human speech production and perception.

That was a basis for learning the main historical (and current) approach to feature extraction: log Mel filterbanks and MFCCs.

We briefly covered historical approaches to ASR. The HMM / GMM approach, while no longer the state-of-the-art for ASR, is still relevant in low-resource scenarios.

The state-of-the-art for transcription accuracy is the Transformer model with self-attention, as for many other speech / NLP tasks.

However, streaming (online / continuous) transcription is important in ASR, so the CTC approach -- which initiated the deep learning revolution in ASR - is still very relevant.

Finally, while ASR has not traditionally been a part of NLP, it has the same concerns - interpretation and transformation of linguistic content. ASR, NLP, and other speech processing tasks are becoming increasingly close with the recent advances of generative AI and natural ways of interacting with computer systems.