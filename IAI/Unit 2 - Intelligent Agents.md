Intelligent agents are at the core of AI, designed to perceive environments and take actions to achieve specific goals. These agents interact with their surroundings via sensors (perception) and actuators (action)

## Agents and Environments
### Agent Definition:
- An **agent** perceives its environment through sensors and acts upon it using actuators.
- **Percept**: Input the agent receives at any moment
- **Percept Sequence**: The complete history of what the agent had perceived.
- **Agent Program**: Operates in cycles of perceiving, thinking, and acting rationally.

### Agent Components:
- ###### Sensors: Detect changes in the environment. Examples:
	- Human agent: Eyes, ears.
	- Robotic agent: Cameras, infrared sensors
	- Software agent: Keystrokes, file content

- ###### Actuators: Enable actions in the environment. Examples:
	- Human agent: Hands, legs
	- Robotic agent: Motors, grippers
	- Software agent: Display output, send packets

- ###### Example: Vacuum-Cleaner World
	- Environment: Two locations (A and B)
	- Percepts: Location and status (e.g., [A, Dirty])
	- Actions: Move Left, Move Right, Suck Dirt, No Operation (NoOp)

## Rational Agents
### Definition:
- A rational agent chooses actions that maximise the performance measure based on its percept sequence.
### Performance Measures:
- Define the success of an agent's behaviours. Examples for a vacuum cleaner:
	- Amount of dirt cleaned within a timeframe
	- Cleanliness of the floor
	- Efficiency of electricity usage
### Task Environment Considerations:
- Must analyse the PEAS elements:
	- **Performance** Measure: Defined success criteria
	- **Environment**: The agent's surroundings
	- **Actuators**: Tools the agent uses to perform actions
	- **Sensors**: Devices used to gather input

### Example: Internet Shopping Agent
- **Performance** Measure: Cost Savings, Quality of recommendations
- **Environments**: Websites, Vendors
- **Actuators**: Navigating websites, filling forms
- **Sensors**: HTML page content, user unput

## Environment Types
### 1. Fully Observable vs Partially Observable
- Fully observable: Agent perceives all necessary info (e.g. Chess)
- Partially observable: Requires informed guesses (e.g. Taxi driving)
### 2. Deterministic vs Stochastic
- Deterministic: Next state is predictable (e.g. Rubik's Cube)
- Stochastic: Outcomes involve randomness (e.g. Poker)
### 3. Episodic vs Sequential
- Episodic: Actions are independent (e.g. Image recognition)
- Sequential: Actions influence future states (e.g. Robot navigation)
### 4. Static vs Dynamic
- Static: Environment does not change during deliberation (e.g. Crossword puzzles)
- Dynamic: Environment changes continuously (e.g. Football robots)
### 5. Discrete vs Continuous 
- Discrete: Finite states (e.g. Board games)
- Continuous: Infinite states (e.g. Driving)
### 6. Single Agent vs Multi Agent
- Single Agent: Operates alone (e.g. Maze solving problem)
- Multi-Agent: Interacts with other agents (e.g. Self-driving cars on shared roads)

## Agent Types
### 1. Simple Reflex Agents:
- Base decisions on current percept without history.
- Work in fully observable environments
- E.g. Room cleaning robot using condition-action rules
- Limitations:
	- Cannot handle partially observable environments
	- Limited adaptability and intelligence
### 2. Model-Based Reflex Agents
- Use a model to represent the world
- Keep track of the internal state based on percept history
- Handle partial observability by predicting unseen parts of the world
- E.g. Mars rover avoiding redundant sample collection
### 3. Goal-Based Agents:
- Take decisions to reduce the distance from a defined goal
- Require explicit goal representation, enabling flexibility
- E.g. Mars lander adjusting power levels to climb a hill
### 4. Utility-Based Agents:
- Consider the "happiness" (utility) of achieving a goal
- Choose actions that maximise utility
- E.g. Mars rover selecting the safest and most efficient route
### 5. Learning Agents:
- Improve performance over time through experience
- Composed of:
	- **Learning element**: Adjusts behaviour based on feedback
	- **Performance Element**: Executes decisions
- E.g. GPS Systems re-routing based on traffic data

## PEAS Analysis Examples:
### Automated Taxi:
- **Performance Measure**: Safety, destination accuracy, comfort
- **Environment**: Roads, weather, traffic
- **Actuators**: Steering, brake, accelerator
- **Sensors**: Cameras, GPS, accelerometers

### Medical Image Processing Agent:
- **Performance** Measure: Highlighting biologically relevant parts.
- **Environment**: Medical images (e.g., CT, MRI).
- **Actuators**: Highlight features in images.
- **Sensors**: Colour pixel arrays.