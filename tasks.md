## Add a 'seed' Function

In `gameoflife.js` add a function named `seed` that returns its arguments in an array. That is, if the function is called with three arguments (`seed(a,b,c)`) it should return an array containing the three arguments (`[a,b,c]`). Use the `arguments` object to achieve this. Ensure that the function `seed` is exported from the module.

## Add a 'same' Function

We need to be able to test if two cells are the same. Add a function named `same` that accepts two cells (a cell is represented as an array with two integer values) and returns a Boolean indicating if the two cells are the same. Ensure that `same` is exported from the module.

## Add a 'contains' Function

The game state of the cells is represented by an array containing all living cells. For example, `[[3,4], [4,4]]`. All other cells are not alive. 

Add a function named `contains` that tests if the supplied cell is alive in the passed game state. The cell to test for must be passed as a function parameter. The game state must be passed as the `this` value within the `contains` function. Note that this is not a recommended way to implement a function because it hides the state parameter from consumers. It is done here to demonstrate the language feature. Ensure that `contains` is exported from the module.

## Add a 'sum' Function

Add a single-line arrow function function named `sum` that adds together two cells. The first coordinate of the result is the sum of the first coordinates of the two summed cells. The second coordinate of the result is the sum of the second coordinates of the two summed cells. That is, [a,b] + [c,d] = [a+c, b+d]. Ensure that `sum` is exported from the module.

## Add a 'printCell' Function

Add a function `printCell` with two parameters. The first is a cell (the corresponding argument, for example, would be of the form `[x,y]`), and the second is a game state (array of cells). If the cell is alive in the game state the function returns ▣ ('\u25A3'), otherwise it returns ▢ ('\u25A2'). The `contains` function created previously is also an object. To determine if the cell is alive, invoke the `contains` function by calling its `call` method (`contains.call(...)`) to set the `contains` function's `this` value to the game state. Ensure that `printCell` is exported from the module.

## Add a 'corners' Function

Add a function `corners` that calculates the top-right and bottom-left coordinates of the rectangle that contains all living cells. The function should have a single parameter which is the game state. If no argument is passed, the argument should default to an empty game state (`[]`) using a default parameter. The return value of the function should be an object with two properties, `topRight` and `bottomLeft`. For example, `{topRight: [x,y], bottomLeft: [x,y]}`. If there are no living cells, the `topRight` and `bottomLeft` should both be `[0,0]`. Ensure that `corners` is exported from the module.

## Add a 'printCells' Function

Add a function `printCells` that uses the `printCell` and `corners` functions created previously to build a string representation of the game state. `printCells` takes one array parameter of cells. It should output the rectangle of cells defined by the `bottomLeft` and `topRight` values returned from `corners`. For each cell position, it should output the value returned from the `printCell` function. Print a space character between each cell in each row. Print a newline character at the end of each row (including the last row).

For example, `printCells([[3,2],[2,3],[3,3],[3,4],[4,4]])` should return `"▢ ▣ ▣\n▣ ▣ ▢\n▢ ▣ ▢\n"` and, `console.log(printCells([[3,2],[2,3],[3,3],[3,4],[4,4]]))` should output

```
▢ ▣ ▣
▣ ▣ ▢
▢ ▣ ▢
```

Ensure that `printCells` is exported from the module.

## Add a 'getNeighborsOf' Function

Add a function `getNeighborsOf` that returns an array containing all of the neighbors of a given cell. A cell always has exactly eight neighbors. Consider the cell `[2,2]`. 

```
[1,3] [2,3] [3,3]
[1,2] [2,2] [3,2]
[1,1] [2,1] [3,1]
```

Note that the neighbors of `[2,2]` are `[[1,1], [2,1], [3,1], [1,2], [3,2], [1,3], [2,3], [3,3]]`. The neighbors of a cell can be calculated by using the `sum` function created previously to add offsets to the cell. For example, the cell to the left of a given cell can be found by adding `[-1,0]`. Thus the cell to the left of [2,2] is `sum([2,2], [-1,0])`.

Ensure that `getNeighborsOf` is exported from the module.

## Add a 'getLivingNeighbors' Function

Add a function `getLivingNeighbors` that returns the living neighbors of a given cell within a given game state. The function should have two parameters. The first is a cell (the corresponding argument, for example, would be of the form `[x,y]`), and the second is a game state (array of cells). The function should return an array containing all living cells that are neighbors of the cell that is the first function parameter. Use the `contains` function created previously to check if a neighboring cell is alive. Call `contains` by first using its `bind` method to set the current game state as the value of `this` within `contains`. 

Ensure that 'getLivingNeighbors' is exported from the module.

## Add a 'willBeAlive' Function

Add a function `willBeAlive` that calculates if a given cell will be alive in the next game state. The function should have two parameters. The first is a cell (the corresponding argument, for example, would be of the form `[x,y]`), and the second is a game state (array of cells). A cell is alive in the next game state if and only if:

* the cell has three living neighbors, or,
* the cell is currently alive and has two living neighbors

Use the function `getLivingNeighbors` created previously to determine how many living neighbors the cell currently has. Use the function `contains` created previously to determine if the cell is currently alive. Invoke the `contains` function by using its `call` method to supply the current game state as the `this` value within `contains` and call the function. 

Ensure that 'willBeAlive' is exported from the module.

## Add a 'calculateNext' Function

Add a function `calculateNext` that calculates the next state of the game from the current state of the game. The function should have a single parameter `state` that is an array containing all living cells (the current game state). The function should return an array containing all living cells in the next game state.

Ensure that `calculateNext` is exported from the module.