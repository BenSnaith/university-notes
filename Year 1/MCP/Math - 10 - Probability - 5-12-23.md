- Support Video Notes
    
    ## Probability
    
    Probability is the likelihood of something occurring, measured with a decimal value with 0 being impossible and 1 being certain we of course have every decimal in between these to work with.
    
    Let’s take a standard six sided die, assuming the die is fair, then the probability of rolling any standard value is 1 in 6, to reach our decimal value that is 1 / 6 = 0.167, the probability of not rolling that number is 5 / 6 = 0.833.
    
    The probability of rolling an even number is 3 / 3 = 0.5 and the same goes for rolling a not even number.
    
    The probability of rolling a square number is 2 / 6 = 0.333 and not rolling a square number is,  
    4 / 6 = 0.667  
    
    In each of these situations the probabilities add up to exactly one as we are certain that the die will provide a number
    
    Similarly we can look at a Roulette wheel, there are 37 slots where; 18 are black, 18 are red and 1 is green.
    
    The sample space (denoted by Ω) is what we call all of the possibilities and this is a set comprising of 37 numbers (in this case), the red numbers are a subset of the sample space.
    
    To determine the probability of landing in a red slot we divide the number of elements in the red subset by all the elements in the sample space to get; 18 / 37 = 0.486
    
    The ball landing in a red spot is an EVENT and each EVENT has a COMPLIMENT which is the ball not landing in a red slot.
    
    We can calculate this in two ways, we could divide the number of all the non-red slots by the total number of slots; 19 / 37 = 0.514.
    
    Or we can subtract our red probability from 1; 1 - 0.486 = 0.514.
    
    Either one should give us the same answer and the probabilities of red and not red should add up to one as the all is certain to land somewhere.
    
    ![[Untitled 20.png|Untitled 20.png]]
    
    Say we want to find the probability of the ball landing in either, slots 10 to 15 (inclusive) or in 20 to 30 (inclusive) since we are saying subset A or subset B, that is a union operation;
    
    P(A u B)
    
    We calculate this using addition
    
    A. 6 / 37 = 0.162
    
    B. 11 / 37 = 0.297
    
    By adding these two values together, the probability of this being a winning bet is 0.459
    
      
    
    How about what is the probability of the ball landing in either a slot higher than 10, or a red slot.
    
    There are 26 slots > 10 giving a probability of; 26 / 37 = 0.703
    
    There are 18 red slots giving a probability of; 18 / 37 = 0.486
    
    These probabilities add up to more than one and probabilities are never more than one so a mistake has been made, the probability cannot be 1 either as the probability of this is not certain.
    
    The problem is that we have counted some of the slots twice in determining the probability, some of the slots that are above 10 are also red so we have counted them twice, there are several ways to deal with this.
    
    We might add the number of red slots to the number of slots above 10 and ten subtract the amount that fall into both; 18 + 26 - 13
    
    We then divide by 37 which gives us; 0.838
    
    Alternatively we might calculate the probability of losing this bet and then subtracting the number from 1
    
      
    
    We are going to continue exploring the idea of probability by using a pack of cards, what is the probability of picking a card at random from a pack and having that card be an ace.
    
    4 / 52 = 0.077
    
    What is the probability of drawing two consecutive aces from a pack, an ace and then another ace, here AND = n and we multiply.
    
    4 / 52 * 3 / 51 = 0.00452
    
    ## Conditional Probability
    
    This is the likelihood of some outcome, based on some previous outcome.
    
    Example: our population contains adults and children, it also consists of people who are gamers and people who are not, there are 4 categories of people
    
    We could ask the question, what is the probability that the a person chosen at random is a gamer.
    
    Well there is a sample space of 40 and 20 are gamers, 20 / 40 = 0.5
    
    Lets look at the probability that a person chosen at random is a child and not a gamer.
    
    Once again our sample space is 40 and now only 5 meet the criteria; 5 / 40 = 0.125
    
    But what if we already know something about the person that has been chosen, we might know for example, that they are an adult.
    
    A question here could be, What is the probability that a person is a gamer, given that they are an adult, the nature of this question changes our sample space. It’s no longer 40, it’s 25 as all of the children have been eliminated, 10 of our 25 are gamers so the probability; 10 / 25 = 0.4
    
      
    
    Bayes’ Theorem:
    
    P(B | A) = P(A | B) P(B) / P(A)
    
    ![[Untitled 1 9.png|Untitled 1 9.png]]
    
    We will need some information to substitute into this equation.
    
    We know the probability of them being a child is; 15 / 40 = 0.375
    
    We also know that the probability of someone being a gamer is  
    20 / 40 = 0.5  
    
    A = 0.5
    
    B = 0.375
    
    Given a person is a child, their probability of being a gamer is  
    10 / 15 = 0.66 (this is A given B)  
    
- Lecture Notes
    
    ## Probability
    
    - The likelihood of some outcome
    - Expressible in different ways:
    
    1 in 10
    
    1/10
    
    10%
    
    0.1
    
    - 0 is impossible, 1 is certain
    - The set of all possible outcomes is called the sample space
    - This is signified by Omega: Ω
    - This means that P(Ω) = 1
    
    (the probability that there will be an outcome is 100%)
    
    ## Why do we care?
    
    - We need to be able to determine probabilities
    
    “The system provides 99% reliability … “
    
    - How reliable is our system.
    - We need to be able to manufacture probabilities:
        - Games development
        - Simulation modelling
        - Data mining
        - Machine Learning
        - Sorting Algorithms
    
    ## Complement
    
    - The complement of an outcome is “the probability that the outcome will not occur”.
    - For an outcome A:
        - P(A) = the probability of that outcome occurring
        - P(!A) = the probability of that outcome not occurring
    - P(A) + P(!A) = 1
    - The probability of rolling a six on a dice ( 1 / 6 ) is 0.167
    - The probability of not rolling a six is 0.833
    - The probability of rolling either a six or something else is 1
    
    ## Birthday Problem
    
    ## Sniper Rifle
    
    ## One event or another
    
    - A bag contains marbles that are red (R), blue (B), and green (G). The probability of taking a marble, at random, which is red or blue can be written as P(R) + P(B) or P(R u B)
    - It’s only this straightforward because no marble is both red and blue
    
    ![[Untitled 2 9.png|Untitled 2 9.png]]
    
    - In a game of roulette, if I want to calculate the probability of the ball landing on a red number or an odd number, there is an overlap, since some numbers are both red and odd
    
    ![[Untitled 3 7.png|Untitled 3 7.png]]
    
    - In a game of roulette, if I want to calculate the probability of the ball landings on a red number or an odd number, there is overlap, since some number are both red and odd
    - P(R) + P(O) - P(R n O)
    
    ![[Untitled 4 6.png|Untitled 4 6.png]]
    
    ## One event and another
    
    - In a game of roulette, if I want to calculate the probability of two consecutive red numbers on two consecutive plays
    - P(R$_1$﻿) n P(R$_2$﻿)
    
    ## Venn Diagram
    
    ![[Untitled 5 6.png|Untitled 5 6.png]]
    
    ![[Untitled 6 4.png|Untitled 6 4.png]]
    
    ![[Untitled 7 3.png|Untitled 7 3.png]]
    
    ![[Untitled 8 3.png|Untitled 8 3.png]]
    
    ![[Untitled 9 2.png|Untitled 9 2.png]]
    
    ## One event AND another
    
    ![[Untitled 10 2.png|Untitled 10 2.png]]
    
    ## The National Lottery
    
    ![[Untitled 11 2.png|Untitled 11 2.png]]
    
    ## Conditional Probability
    
    - This means the probability is altered by some previous event
    - For example, the probability of the second marble being blue depends upon the colour of the first marble
    - What is the probability of the ball landing on a black number given that the previous nine numbers were red?
    
    ## Independent events
    
    - If the probability of one event has no bearing on the probability of another event, they are independent events
    - For example, when rolling a die, the probability is not influenced by the previous role of the die
    
    ## Bayes Theorem
    
- Lecture Points
    
    What is the probability that the next number is black given that the precious nine numbers were red.
    
    18 / 37 =
    
    The given that the previous nine were red is absolutely irrelevant and has no bearing on the next, this is a common misconception
    
    ![[Untitled 12 2.png|Untitled 12 2.png]]
    
- Trev Tutor
    
    S is a set called the Sample Space
    
    E is a subset of S called an Event
    
    the probability of an event occurring is:
    
    $P(E) = E/S$﻿
    
      
    
    Jane tosses two fair coins, what is the probability of getting _exactly_ one head.
    
    S, Sample Space
    
    S = { HH, HT, TH, TT }
    
    E = { HT, TH }
    
    E / S
    
    2 / 4 == 1 / 2
    
      
    
    Given A we can find A compliment, or everything not A
    
    What is the probability of not getting 2 heads
    
    P(2 heads) = { HH } / 4 = 0.25
    
    P(!2 heads) = 1 - P(2heads) = 0.75
    
      
    
    Given a deck of 52 cards we draw 5. What is the probability of getting
    
    a) 3 Aces, 2 Jacks
    
    4 aces so out of the 4 we choose 3 = (4 / 3)
    
    4 jacks so out of the 4 we choose 2 = (4 / 2)
    
    4 / 3 x 4 / 2 // 52 / 2
    
      
    
    I toss a coin and then roll a 6-sided die, what is S