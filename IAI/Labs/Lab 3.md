### Intelligent Agents

This lab develops an intelligent agent for the vacuum cleaner problem.

### Creating Environment

Our environment is a square grid, where each cell may or may not be dirty. The size of the grid (env_size), the initial states of the cells (init_status), and the initial location of the vacuum cleaner (init_loc) can be determined by the user. The init_status is matrix of size (env_size * env_size), where the (i, j)-th element shows the dirty state of the cell in the i-th row and j-th column. Each element of init_status can take two values 0 and 1, where 0 means clean and 1 means dirty.

The figure below shows how number rows and colums where n = 3. We follow the same pattern for n != 3. That is, we number the rows from top to bottom and columns from left to right starting with 0.

![[Pasted image 20241121193256.png]]

To create this environment, we need to take some inputs from the user. To this end, we use the Python built-in `input()` function takes the input from the user and converts it into a string. The type of the returned object always will be `<type 'str'>`. So for taking integer input we have to type cast those inputs into integers by using Python's built-in `int()` function.

Run the following example to see how these two functions work, You can give any integer number (e.g. 100) as the input.