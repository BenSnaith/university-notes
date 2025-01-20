###### Search is a fundamental technique in AI to solve problems where an agent systematically explores a problem's state space to find a solution. It involves problem formulation, search strategies, and evaluation of algorithm efficiency.

## Key concepts
### 1. Goal-Based Agents vs. Reflex Agents
- Reflex agents respond directly to stimuli with pre-defined rules (e.g. if dirty, clean)
- Goal-based agents perform action to achieve specific objectives using search and planning
### 2. Abstraction in Search
- Simplifies the representation of real-word problems to make them computationally tractable

## Problem Formulation
### Five components:
#### 1. **Initial State**: Describes the starting condition
#### 2. **Actions**: Defines all possible moves the agent can take
#### 3. **Transition Model**: Specifies the outcome of actions
#### 4. **Goal Test**: Determines if the goal has been reached
#### 5. **Cost Function**: Assigns a cost to each step (e.g. distance, time)
### Example: 8-Puzzle Problem
- Initial State: Layout of numbered tiles and blank spaces (e.g. 8, blank, 6, 5, 4, 7, 2, 3, 1)
- Actions: Move blank space (up, down, left, right)
- Transition Model: Updates tile positions based on moves.
- Goal Test: Determines if the layout matches (blank, 1, 2, 3, 4, 5, 6, 7, 8)
- Cost Function: One move = cost of 1
### Example: Travel-Planning Website
- Goal: Travel from Birmingham to Doncaster
- States: Each city represents a state
- Initial State: "City: Birmingham"
- Actions: Travel between cities
- Transition Model: Updates current city to destination
- Goal Test: Determines if the state is "City: Doncaster"
- Cost Function: Measures time or monetary cost

## Search Trees and State Spaces
### Search Tree Components:
- **Nodes**: Represent states
- **Edges**: Represent actions leading to new states
- **Initial Node**: Root of the tree
- **Goal Node**: Node satisfying the goal test
### Challenges:
- **Repeated States**: Must avoid revisiting the same state
- **State Explosion**: The size of the tree can grow exponentially with branching factor (b) and depth (d)
### Example: Vacuum Cleaner Problem
- State Space: All possible configurations of dirt and agent location
- Actions: Move left/right, clean

## Evaluating Search Algorithms
### Search strategies are evaluated based on:
1. **Completeness**: Does it always find a solution if one exists?
2. **Time Complexity**: Number of nodes generated/expanded
3. **Space Complexity**: Maximum number of nodes held in memory
4. **Optimality**: Does it always find the least-cost solution?
### Complexity Metrics:
- b: Branching factor (maximum children per node)
- d: Depth of the shallowest goal
- m: Maximum depth of the tree
## Types of Search Algorithms
### 1. Uninformed Search (Blind Search)
- No information about goal distance or path cost
#### Breadth-First Search (BFS):
- **Strategy**: Explore all nodes at one depth before moving deeper
- Properties:
	- Completeness: Yes
	- Time Complexity: O($b ^d+^1$) BFS Consumes much time to reach the goal node for larger instances
	- Space Complexity: O($b ^d+^1$) Requires a huge amount of memory
	- Optimality: Yes (if path costs are uniform)
- Example: Exploring a graph by level

#### Depth-First Search (DFS):
- Strategy: Explore as deep as possible along each branch before backtracking
- Properties:
	- Completeness: No (may fail in infinite-depth spaces)
	- Time Complexity: O($b^m$): Terrible if m is much larger than d
	- Space complexity: O($bm$) i.e. linear space
	- Optimality: No
- Example: Navigating a maze deeply along one path before exploring others
**$b$** - maximum branching factor of search tree
$d$ - depth of the least-cost solution
$m$ - maximum depth of the state space (may be infinite)
### 2. Informed Search (Heuristic Search)
- Uses heuristic functions to guide search towards the goal
- Example algorithms:
	- Greedy Best-First Search: Chooses nodes based on heuristic estimates
	- A*: Combines heuristic with path cost to ensure optimality

## BFS vs DFS

| **Feature**          | **BFS**                               | **DFS**                           |
| -------------------- | ------------------------------------- | --------------------------------- |
| **Completeness**     | Always finds a solution if one exists | May fail in infinite-depth spaces |
| **Time Complexity**  | O($b ^d+^1$)                          | O($b^m$)                          |
| **Space Complexity** | O($b ^d+^1$)                          | O($bm$)                           |
| **Optimality**       | Yes (for uniform costs)               | No                                |
| **Preferred When**   | Shallow solutions, low branching      | Many goal states, deep trees      |
## Challenges in Search
### 1. Tree Size: Exponential growth with b and d
### 2. Unknown Depth/Shape: Algorithms must handle incomplete knowledge of the tree structure