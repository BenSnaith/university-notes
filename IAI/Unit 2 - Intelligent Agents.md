## Unit Outline

- Agents and environments.
- Rationality and rational agents.
- PEAS (Performance Measure, Environment, Actuators, Sensors) Analysis.
- Environment Types.
- Agent Types.

## Agents and Environments

- An agent is anything that can be viewed as
    - **Perceiving** its **environment** through **sensors** and
    - **Acting** upon that **environment** through **actuators**
- **Percept**: Agent’s perceptual input at any given instant
- **Percept Sequence**: Complete history of everything the agent has ever perceived.
- An agent’s choice of action at any given instant can depend on the entire percept sequence observed to date.
- An **agent program** runs in cycles of: (1) Perceive, (2) Think and (3) Act rationally.
- Assumption: Every agent can perceive its own actions (but not always the effects)

## Sensors and Actuators

- Sensors: Sensor is a device which detects the change in the environment and sends the information to other electronic devices. An agent observes its environment through sensors.
- Actuators: Actuators are the component of machines that converts energy into motion. The actuators are only responsible for moving and controlling a system. An actuator can be an electric motor, gears, rails, etc.

## Types of Agents

- Human agent:
    - eyes, ears, and other organs for sensors
    - hands, legs, mouth, and other body parts for actuators.
- Robotic agent:
    - cameras and infared range finders for sensors
    - various motors from actuators
- A software agent:
    - Keystrokes, file contents, received network packages as sensors.
    - Displays on the screen, files, send network packets as actuators.

## Agent Functions and Programs

- An agent’s behaviour is described by the agent function which maps from percept histories to actions:
    - f: P* → A
- Aim: find a way to implement the rational agent function concisely → design an agent program.
- **Agent = agent program + architecture**
- **Architecture**: Some sort of computing device with physical sensors and actuators (PC, robotic car)
- **Agent program**:
    - Taken the current percept as input from the sensors
    - Return an action to the actuators
- While agent function takes the whole percept history, agent program takes just the current percept as input which is the only available input from the environment.
- The agent needs to remember the whole percept sequence, if it needs it.

## Rational Agents

- Rationality:
    - As we discussed last class, “Intelligence” is an ill-defined concept.
- Rational Agent:
    - Chooses actions that maximise the expected value of the performance measure given the current percept sequence.
- Agent percept's → Action sequences → Environmental changes
    - If the sequence of states that changed the environment is desirable, then the agent did it’s job.
- This can be measured using a metric called performance measure.
- Performance measure: An objective criterion for success of an agent’s behaviour.

## PEAS Analysis (Performance Sensors, Environment, Actuator, Sensor)

- When building a rational agent, task environment must be considered.
- The task environment is made up of PEAS
    - Performance Measure: the unit to define the success of an agent.
    - Environment: is the surrounding of an agent at every instant. It keeps changing with time if the agent is set in motion.
    - Actuator: is a part of the agent that delivers the output of an action to the environment.
    - Sensor: are the repetitive parts of an agent which takes the input from the agent.

## Example

- Internet Shopping Agents (ISAs) allow consumers to costless-ly search many online retailers and buy at the lowest price.

  

- Performance Measure:
    - Price, Quantity, Appropriateness, Efficiency
- Environment
    - Current and Future: Websites, Vendors and Shippers.
- Actuators
    - Display to the user, follow URL, fill in form.
- Sensors
    - HTML pages (text, graphics, scripts)

![[image 5.png|image 5.png]]

## Environment types

- An environment is everything in the world which surrounds the agent, is not part of an agent itself. An environment can be described as a situation in which an agent is present.
- Range of task environment is huge, they can be categorised as follows:
    - Fully Observable (vs Partially Observable)
    - Deterministic (vs Stochastic)
    - Episodic (vs Sequential)
    - Static (vs Dynamic)
    - Discrete (vs Continuous)
    - Single Agent (vs Multi Agent)

## Fully Observable (vs Partially Observable)

- In a fully observable environment, the agent has access to all the necessary information about the environment to make decisions at any point.
- A chess game is fully observable because the agent can see all the pieces on the board at any time.
- Is everything an agent required to choose it actions to it via its sensors?
    - If so, the environment is fully accessible
- If not, part of the environment are inaccessible
    - Agent must make informed guesses about world.
- In decision theory: perfect information vs. imperfect information.

![[image 1 2.png|image 1 2.png]]

## Deterministic (vs Stochastic)

- An environment is deterministic if the next state of the environment is completely determined by the current state and the action taken by the agent.
- A Rubix’s cube is deterministic because any action leads to a predictable result.
- A stochastic environment is one in which the outcome of an action is uncertain and involves probability, there is a degree of randomness or unpredictability in the outcome.
- Most real-world AI environments are not deterministic (Stochastic)
- Stochastic environments:
    - Have aspects beyond the control of the agent
    - Utility functions have to guess at changes in world.

![[image 2 2.png|image 2 2.png]]

## Episodic (vs Sequential)

- In an episodic environment, the agent’s actions are divided into independent episodes, and each action is not dependent on the previous actions.
- Example: Image classification is episodic since classifying one image does not depend on previously classified images.
- Is the choice of the current action dependent on previous actions?
    - If not, then the environment is episodic.
- In non-episodic environments:
    - Agent has to plan ahead:
        - Current choice will affect future actions

![[image 3 2.png|image 3 2.png]]

## Static (vs Dynamic)

- Static environments don’t change.
    - While the agent is deliberating over what to do.
- Dynamic environments do not change.
    - So agent should/could consult the world when choosing actions
    - Alternatively: anticipate the change during deliberation OR make decision very fast.
- Semi-dynamic: If the environment itself does not change with the passage of time but the agent’s performance score does.

![[image 4 2.png|image 4 2.png]]

## Discrete (vs Continuous)

- In a discrete environment, there are a finite number of distinct states, actions, and percept's available
- Example: A turn-based board game like tic-tac-toe is discrete as it involves a limited number of states and actions.
- The environment in which the actions performed cannot be numbered, i.e. is not discrete, is said to continuous.

![[image 5 2.png|image 5 2.png]]

## Single Agent (vs Multiagent)

- An agent operating by itself in an environment or there are many agents working together

![[image 6.png]]

## Environment Types

- The simplest environment is, describe environment?

![[image 7.png]]

- Many real world environments can be:
    - Partially observable, stochastic, non-episodic, dynamic, continuous and multi-agent.

## Agent Structure

- All agents have:
    - Input = current percepts
    - Output = action
    - Program = processes input to produce output
- Agents interact with environment through sensors and actuators

![[image 8.png]]

## Agent Types

- Experts in the field of AI like to classify agents into five types of classes. They do so by the capabilities of each agent. Let’s take a look at each.

  

1. Reflex Agent (simplest): an agent whose actions depends only on the current percept.
2. Model-based Agent: an agent whose action is derived directly from an internal model of the current world state that is updated over time.
3. Goal-based Agent: an agent that selects actions that it believes will achieve explicitly represented goals.
4. Utility-based Agent: an agent that selects actions that it believes will maximise the expected utility of the outcome state.
5. Learning agent (most advanced): an agent whose behaviour improves over time based on its experience.

## Simple Reflex Agents

![[image 9.png]]

- Simple reflex agents select an action based on the current state only ignoring the percept history.
- e.g. If a Mars Rover found a rock in a specific place it needed to collect then it would collect it, if it was a simple reflex agent then if it found the same rock in a different place it would still pick it up as it doesn’t take into account that it already picked it up.
- The Simple reflex agents are the simplest agents.
- These agents take decisions on the basis of the current percepts
- These agents only succeed in the fully observable environment.
- The Simple reflex agent does not consider any part of percepts history during their decision and action processes.
- The Simple reflex agent works on Condition-action rule, which means it maps the current state to action. Such as a Room Cleaner agent, it works only if there is dirt in the room.
- Problems for the simple reflex agent design approach:
    - They have very limited knowledge.
    - They do not have knowledge of non-perceptual parts of the current state.
    - Mostly too big to generate and to store.
    - Not adaptive to changes in the environment.

## Model-based reflex agents

![[image 10.png]]

- Model - knowledgeable about “how the things happen in the world”
- Internal State - It is a representation of unobserved aspects of current state depending on percept history
- Handle partial observability by keeping track of the part of the world it can’t see now.
- e.g. This time our Mars Rover picks up its first sample, and stored this in the internal state of the world around it so it comes across the second same sample it passes it by and saved space for other samples.
- It works by finding a rule whose condition matches the current situation.
- A model-based agent can handle partially observable environments by the use of a model about the world.
- The agent has to keep track of the internal state which is adjusted by each percept and that depends on the percept history.
- The current state is stored inside the agent which maintains some kind of structure describing the part of the world which cannot be seen.
- Updating the state requires information about:
    - How the world evolved independently from the agent, and
    - How the agent’s actions affect the world.

## Goal-based agents

![[image 11.png]]

- Knowing the current state of the environment is not enough. The agent needs some goal information.
- e.g. If our Mars Rover needs to get up a hill, the agent can update it’s knowledge of how much power to put into its wheels to gain certain speeds, through this all relevant behaviours will now automatically follow the new knowledge on moving. However in a reflex agent many condition-action rules would have to be rewritten.
- These kinds of agents take decisions based on how fat they are currently from their goal
- Their every action is intended to reduce its distance from the goal.
- This allows the agent a way to choose among multiple possibilities, selecting the one which reaches a goal state.
- The knowledge that supports its decisions is represented explicitly and can be modified, which makes these agents more flexible.
- They usually require search and planning. The goal-based agent’s behaviour can easily be changed.

## Utility-based agents

![[image 12.png]]

- Sometimes achieving the desired goal is not enough. We may look for the best way to each that goal.
- Agent happiness should be taken into consideration. We call it unity.
- e.g. Let’s show our Mars Rover on the surface of Mars with an obstacle in its way. In a goal based agent it is uncertain which part will be taken by the agent and some are clearly not as efficient as others but in a utility based agent the best path will have the best output from the utility function and that path will be chosen.
- When there are multiple possible alternative, then to decide which one is best, utility-based agents are used.
- They chose actions based on preference for each state. Sometimes achieving the desired goal is not enough.
- We may look for a quicker, safer, cheaper trip to reach a destination. Agent happiness should be taken into consideration.
- Utility describes how “happy” the agent is. Because of the uncertainty in the world, a utility agent chooses the action that maximises the expected utility.
- A utility function maps a state onto a real number which describes the associated degree of happiness.

## Learning agents

![[image 13.png]]

- A learning agent is an AI that can learn from its past experiences or it has learning capabilities. It starts to act with basic knowledge and then is able to act and adapt automatically through learning.

# CHECK THE LECTURE FOR THE EXAM QUESTION.