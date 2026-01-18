## What is (a) language

The system of spoken or written communication used by a particular country, people, community, etc., typically consisting of words used within a **regular grammatical and syntactic structure**.

The method of human communication, usually spoke or written (but also including sign language), consisting of the use of words (or gestures) in a structured and conventional way.

## What is a model / modelling

Something which accurately resembles or represents something else, especially on a small scale, a person or thing that is the likeness of another.

A simplified or idealised description or conception of a particular system, situation, or process often in mathematical terms, that is put forward as a basis for theoretical or empirical understanding or for calculations, predictions, etc; a conceptual or mental representation of something.

Mathematically:

$y = f(x)$

e.g. 

$y = ax + b$

$y$: house value obtained by come multiple
$a$: of
$x$: floor area, plus
$b$: some base value (e.g. minimum price of land or building costs)

In **machine learning**, we learn $f(x)$, i.e., best-fit model (values for $a$ and $b$, in this example) from data:

Many examples of paired $x$ (input) and $y$ (output).

## What is language modelling

The underlying task of language modelling is to predict the probability of a word, or other linguistic forms, in a text based on previously observed text

 - Accepting
	 - Grammar or spelling: is this sentence likely? -> What should we change this to?
		 - "Joey the their legged cat sat on the match"
	 - Speech recognition: suppose we have several hypotheses for a transcription:
		 - "Joey the sea legged cat sat on the mat"
		 - "Joey the three legged cat chat on the mat"
		 - "Joey the three legged cat sat on the mat"
	 - Which should we choose?

 - Predicting (Natural Language Generation)
	 - Large language models, chat-bot dialogue, LLMs work by predicting the next word repeatedly:
		 - "Joey" -> "the" OR "went" OR "giraffe" OR, ...
		 - "Joey the" -> "cat" OR "giraffe" OR "workstation" OR, ...
		 - "Joey the three" -> "leg" OR "arm" OR "student" OR, ...
	 - ... and so on.

## Language Models: Probabilities of text

To model language we need probabilities of text:

```
Pr("Joey the three legged cat sat on the mat) = ?
```

`Pr(-)` denotes "the probability of": `Pr(-) ∈ [0, 1]` (probabilities are 0 ... 1).

*I roll a dice once, what is the probability I roll a six?*

There are 6 possible outcomes, each equally probable: Only 1 of these outcomes gives me a six: the probability is:
`Pr(I roll a 6) = 1 / 6 (~ 0.166)`

*I roll a dice twice: what is the probability the two rolls will total 4*

36 possible outcomes. The 2nd roll is independent of the 1st: (1, 1), (1, 2), (1, 3), ..., (6, 5), (6, 6). Three of these give me total 4: (1, 3), (2, 2), (3, 1): `Pr(total is 4) is 3 * 1 / 16 = 3 / 16 = 1 / 12`

## Estimating probabilities

![[Pasted image 20251023214403.png]]

## Probabilistic Language Models

To model language we need probabilities of text:

```
Pr("Joey the three legged cat sat on the mat") = ?
```

`Pr(-)` denotes "the probability of".

Why?

Language Tasks: 

Grammar or Spelling: `Pr("Joey the their legged cat sat on the match")`
Speech Recognition: `Pr("Joey the sea legged cat sat on the mat")`

Natural Language Generation:

LLMs work by predicting the next word repeatedly:

```
Pr("the" | "Joey")
Pr("three" | "Joey the")
Pr("legged" | "Joey the three")
```

## Conditional Probabilities

![[Pasted image 20251023214922.png]]

## LM Basics: Estimate Counts

Predict the next word:

`Pr(`