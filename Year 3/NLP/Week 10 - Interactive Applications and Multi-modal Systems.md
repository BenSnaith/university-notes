### Interactive NLP - Transformers for all

As we have seen, many NLP tasks - particularly those involving conversational analysis and manipulation, of both text and audio - rather than specific tasks -- have been replaced by Transformers.

Transformers are excellent at modelling long-range dependencies, learning relationships between input features, tokens, and learning from vast amounts of unstructured and even low-quality text or audio.

Text and audio chatbots are not embedded in out of use of computer systems, so we expect to use natural language to deal with modalities beyond text, including audio, image, video, etc. - to generate and / or analyse these modalities.

In this lecture we will show how the basic Transformer architecture underpins all these types of analysis, with relatively minor additions or changes to **data encoding**, input sequence conditioning, or attention.

We will not go into any background of image analysis or generation, because that is outside the scope of NLP. Image and video are only now in scope, in so far as we use natural language to interact with them.

Finally, we will cover state-of-the-art speech / audio chatbots - conversation modelling. This adds an extra layer of complexity - modelling multiple streams in parallel.

![[Pasted image 20251202214538.png]]

### Interactive NLP - Conversational Chatbots

![[Pasted image 20251202214649.png]]

### What is conversation?

"Conversations is an intricate and complex joint activity, and conversations have structure. This is true of all conversations, whether they are conversations between people or conversations between people and language models. Understanding the structure of human conversations is an important social science and linguistic task". (Jurafsky, 2025, chpt. 25)

"Most of the give-and-take of conversation in our everyday life is stereotyped and very narrowly conditioned by out particular type of culture. It is a sort of roughly prescribed social ritual, in which you generally say what the other fellow expects you, one way or the other, to say". (Firth, 1935)

 - Turn taking.
 - Speech acts.
 - Grounding.
 - Sub-dialogues and dialogue structure.
 - Initiative.
 - Inference and Implications.

##### Turn-taking

A conversation is a sequence of turns, but...
 - Turns may overlap.
 - How do we decide when to take a turn, interrupt or correct?
 - Does a pause indicate speaker has finished turn?

##### Speech acts

**Speech acts** or **dialogue acts**: the types of things we say in conversation:

 - Constative: commitment, e.g., conform, deny.
 - Directive: do something, including asking question.
 - Commissive: committing to future course of action.
 - Acknowledgement

##### Grounding

Speech acts are not independent: collective act performed by speaker and hearer.

 - Participants (need to) understand their common ground.
 - i.e., what we agree on.
 - Acknowledging understanding (or not).
 - Often the reason of confirmations ("OK", "umm", "hmm", "of course", ...).
 - And / or repetition and interruptions to seek clarification.

##### Sub-dialogues and dialogue structure

Local and Global:

 - Question: Answer
 - Proposal: Accept / Reject
 - Compliment: Deprecation (Downplaying)
 - May be separated by side-sequences / parentheses / interruptions.
 - To correct or clarify

Humans intuitively understand.

##### Initiative

Who controls the conversation? User or system?

 - Compare interview vs informal chat.
 - Usually mixed - e.g., question - clarifiction - answer.
 - Mixed initiative is hard to model.
 - Why LLM Conversations feels unnatural

##### Inference and Implications

We **don't say everything**, and don't always say what we mean:

 - Implicit comments / questions ("I guess you know...").
 - Implicit responses
	 - "What time do you need to be at...?"
	 - "I have a meetings at 10am".

Shared world knowledge and context.

### What's hard about conversation?

More challenges:

 - How do we make responses naturally varied? What is the balance between repetitiveness and randomness?
 - How do we maintain coherence over a long-term dialogue?

Some of these challenges apply to text-based chats, some apply (or apply more so) to speech-based chats.

### Chatbots

 - **Eliza (1966):**
	 - Pattern-matching using rules to map input phrase to / search for response. No memory or "understanding".
 - **Watson Assistant (2006):**
	 - NLP processing and pattern detection: DeepQA model explores multiple interpretations of question and possible answers, gathers and evaluates evidence.
 - **Siri (2011):**
	 - ASR and deep neural network to classify sounds class - wake word detection - initiate actions.
 - **ChatGPT / Bard (2022-23):**
	 - Text-based transformer LLM, fine-tuned on dialogue datasets, multiple responses re-ranked based on external "knowledge".

##### What is needed?

 - **Understanding meaning:** of words, logical flow or argument, relation to world / shared knowledge.
 - **Understanding user**: (dialogue partner) state.
 - **Coherent management:** of the conversation (local and global structure).

##### Slot-filling

Frame-based or task-based dialogue systems (chatbots) to help a user solve a specific task, e.g., booking a flight. Until recently the commercial state-of-the-art.

**Obtaining meaning:**

Filling a frame consisting of slots filled from a set of values.

Sequence-labelling RNN to extract information:
 - Label roles and spans of text to which they refer.

Additional approaches:
 - Semantic parsing and logical modelling (reasoning). Weights learned from labelled datasets resolve ambiguities.
 - Co-reference resolution (e.g., pronouns).

More general questions:
 - Domain classification: what is the user talking about? - Select appropriate frame(s) - e.g., travel reservations.
 - Intent determination: what is the general goal? - e.g., book a flight.

All (historically) learned from carefully curated and hand-labelled datasets.

**Managing the conversation:**

Iteratively ask questions until slots filled, using pre-written templates.

May use multiople frames, e.g.,

 - Identify destination.
 - Identify route.
 - Hotel reservation, etc.

**Text generation:**

 - AI algorithms to plan and organise sentences.
 - Post-process to finalise the text, e.g., correct tenses, plurals, pronouns.
 - Challenge: ensuring output is naturally varied.

**Understanding the user:**

Dialogue state tracking: keep track of state of (filled) slots and user constraints. Decide which speech act to take next:

Markov Decision Process: probabilistic modelling of user intentions and the conversation:

 - **States**: which slots are filled?
 - **Actions**: e.g., query for information.
 - **Transition function**: what action to perform next.
 - **Policy**: Which action to take next for the most reward (e.g., progress to completion).

The real world is uncertain: Partially-observable Markov Decision Process (POMDP) maintains a probability distribution over the states, indicating its current knowledge / belief about which state it is in. Better able to handle mis-understandings.

##### Transformer-Based

Text LLM transformer architecture:

e.g., ChatGPT, Google Bard:

 - Language model pre-trained on very large amount of text to gain a good general "understanding" of language.
 - Transfoermet architecture allows for long-range context (and attention across the context).
 - Fine-tuned on dialogue datasets of public conversations.
 - Generate multiple potential responses, re-rank according to safety filling, grounding in external knowledge.

Conversational ability is purely data-driven: natural responses arise from replicating data an patterns seen in training.

### Reinforcement

**LLM instruction turning and bias removal:**

Reinforcement Learning from Human Feedback (RLHF)

 1. Create human-generated prompts and responses.
 2. Pre-train a LLM and fine-tune as usual.
 3. Humans score multiple responses from the LLM: usually comparing prompts.
 4. Train a separate reward model on this human scoring process - may be another language model.
 5. Iteratively fine-tune the LLM with Proximal Policy Optimisation (PPO) - a reinforcement learning algorithm - usually only a subset of parmeters.
 6. The final model is tuned to choose output that would maximise the reward - i.e., human-preferred.

![[Pasted image 20251203213621.png]]
![[Pasted image 20251203213632.png]]

### Audio

The classic approach to a turn-taking audio chatbot is a sequential model:

1. Voice Activity Detection (VAD) - e.g., wake-word ("Hey Google").
2. Speech Recognition (speech to text - STT / ASR) - transcribe user's voice input
3. Text LLM implicitly doing all of the following:
	- Spoken Language Understanding (SLU),
	- Dialogue State Tracking (DST),
	- Natural Language Generation (NLG - response)
 4. Speech Synthesis (text-to-speech - TTS) - audio reply.

Problems:

 - Latency - seconds delays means poor user experience - natural conversation expects 200-300ms latency.
 - Turn-based - no allowance of overlaps, interruptions, etc.
 - Loss of non-linguistic info - emotion, environment noise, accent, etc.

### Speech Synthesis (TTS)

Speech Synthesis / Text-to-Speech (TTS)

Translating text input (words, sentences) to audio output.
##### Goal

Natural, personalised, emotional, realistic audio.
##### History

 - Atriculatory systhesis - simulation of the human vocal tract - mechanical and digital.
 - Concatenative speech synthesis.
 - Statistical parametric speech synthesis.
 - Deep learning.
 - State of the art - personalised zero-shot speech synthesis using transformers.

### Mechanical Atriculatory Synthesis

![[Pasted image 20251203215018.png]]

Digitally simulate the air flow through the human speech production system. Data obtained from 2-dimensional x-rays; not precisely modelled. Therefore the synthesised speech is intelligible but lacks naturalness.

### Concatenative Synthesis

Unit selection: select short sections of speech from a corpus containing many examples for each. Needs a lot of data, carefully recorded and labelled phones (phonemes) and diphones.

Not very controllable (synthesised reading-style voice). Some pitch adaption to change the prosody is possible through the Pitch synchronous overlap add (PSOLA) to change prosody.

Tends to sound unnatural due to limitations in obtaining all examples, and concatenating them correctly.

### Statistical Parametric Synthesis

Early: formant synthesis, Rule-based: models the degree of voicing (e.g., between vowel and consonant), f0 ("pitch" - e.g., male vs female), formant frequencies & amplitude.

Sounds intelligible but robotic-sounding.

HMMs model spectral features directly and convert to waveform. Less data needed, and able to model various speaking styles, but speech tends to be muffled due to statistical averaging.

### Deep Learning

Deep learning develops statistical parametric synthesis with better modelling.

WaveNet (Google DeepMind, 2016) modelled the waveform directly to generate one sample at a time using a Recurrent Convolutional Neural Networks.

Through training on very large data (recordings from real speakers), able to vary gender, language and accent.

Tacotron2 (Google, 2018) represented significant progress. Characters modelled directly using a sequence-to-sequence model. Mel Spectrum output is converted to Waveform in a second stage.

### Transformers - Text Processing

![[Pasted image 20251203220200.png]]
![[Pasted image 20251203220215.png]]
![[Pasted image 20251203220232.png]]

### Transformers - ASR

Sequence modelling can potentially be applied to any type of data, if we can encode it as discrete tokens.

ASR: Audio encoder such as HuBERT or Wav2Vec 2.0 maps raw speech features (Mel filterbacks or MFCCs) to discrete features using Self-supervised learning and Vector Quantisation to create a codebook of linguistically meaningful features.

(These lose details of the audio that are not relevant for ASR).

These audio tokens are used to condition the text prediction via the cross-attention mechanism.

### Self-supervised Learning (SSL)

Self-supervised learning is learning patterns in data without explicit labelling - the algorithm creates its own labels. 

Self-supervised learning of speech representations aims to solve two problems with ASR:

 1. Huge acoustic models perform well but only if they have enough data of good enough quality to train well: If some of the acoustic modelling can be done without labelled data, with would reduce the data dependency.
 2. 

