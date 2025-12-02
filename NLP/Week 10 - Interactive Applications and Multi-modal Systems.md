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



