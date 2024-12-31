## Problem Formulation Examples
### 1. Tower of Hanoi
- Initial State: All disks are stacked on the first tower
- Actions: Move the top disk from one tower to another
- Transition Model: Updates the position of the disks after each move
- Goal Test: All disks stacked on the third tower in correct order.
- Cost Function: Number of moves
### 2. Sudoku
- Initial State: A partially filled 9x9 grid
- Actions: Fill in empty cells
- Transition Model: Updates the grid after filling a cell
- Goal Test: Grid satisfies sudoku rules
- Cost Function: Number of filled cells or time taken
### 3. 8-Queens Problem
- **Initial State**: No queens on the board
- **Actions**: Place a queen in any row/column
- **Transition Model**: Updates the board
- **Goal Test**: All 8 queens are placed without attacking each other
- **Cost Function**: Number of placements

## Search Algorithms Cont.
### Depth-Limited Search (DLS)
- DFS with a depth limit.
- Properties:
	- Completeness: No (if the depth limit is too small)
	- Optimality: No
	- Time Complexity: O($b^l$) where l is the depth limit
	- Space Complexity: O($bl$) where l is the depth limit
### Iterative Deepening Search (IDS)
- Repeatedly performs DLS with increasing depth limits
- Properties:
	- Completeness: Yes
	- Optimality: Yes, for uniform costs
	- Time Complexity: O($b^d$)
	- Space Complexity: O(bd)

$b$ - maximum branching factor of the search tree  
$d$ - depth of the least-cost solution  
$m$ - maximum depth of the state space (may be ∞)

## Informed Search Strategies
### 1. Heuristic Function ()
- Estimate of the cost to reach the goal from node.
- Must be admissible (never overestimates)
### 2. Greedy Best-First Search
- Attempts to find the most promising path from a given starting point to a goal.
- Properties:
	- Completeness: No, can get stuck in loops
	- Optimality: No
	- Time complexity: O($b^m$) But a good heuristic can give dramatic improvement of average cost
	- Space Complexity: O($b^m$)
- E.g. Finds paths based on heuristic estimates (e.g. straight-line distance)
### 3. A* Search 
- Combines path cost and heuristic
- Properties:
	- Completeness: Yes
	- Optimality: Yes
	- Time Complexity: O($b^d$) - Exponential but a good heuristic can give dramatic improvement of average cost
	- Space Complexity: O($b^d$)

## Practical Examples
### Pathfinding in games
- Breadth-First Search: Effective for small grids without obstacles
- Greedy Best-First Search: Quickly locates goals but may find suboptimal paths
- A* Search: Balances speed and optimality, widely used in game AI
### 8-Puzzle Heuristics
- Number of Misplaced Tiles: Counts tiles not in their goal position
- Manhattan Distance: Sum of distances of tiles from their goal positions