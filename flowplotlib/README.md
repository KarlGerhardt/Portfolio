### `elements.py` File Description

The `elements.py` script contains classes for creating and rendering various types of elements typically found in a flowchart. Utilizing the `matplotlib` library, these classes facilitate the drawing of shapes and text on a plot to visually represent the flowchart elements.

#### Classes Included:

1. **FlowElement:**
    - _Description:_ Serves as the base class for all flowchart elements.
    - _Attributes:_
        - `label`: The displayed text on the flowchart element.
        - `x`, `y`: Coordinates for positioning the element.
        - `grid_position`: Grid coordinates for alignment and connections.
    - _Methods:_
        - `set_position(x, y, grid_position)`: Assigns position to the element.
        - `draw(ax, x, y, text_size)`: A placeholder, meant to be overridden by subclasses for specific rendering instructions.
2. **Process:**
    - _Inheritance:_ Derived from `FlowElement`.
    - _Description:_ Represents a process step in the flowchart, visually rendered as a rectangle.
    - _Methods:_ Overrides the `draw` method to create a rectangle and label on the plot.
3. **StartStop:**
    - _Inheritance:_ Derived from `FlowElement`.
    - _Description:_ Denotes a start or stop point in the flowchart, visually rendered as an ellipse.
    - _Methods:_ Overrides the `draw` method to create an ellipse and label on the plot.
5. **Decision:**
    - _Inheritance:_ Derived from `FlowElement`.
    - _Description:_ Represents a decision point in the flowchart, visually rendered as a diamond.
    - _Methods:_ Overrides the `draw` method to create a diamond and label on the plot.

#### `flowchart.py` File Description

The `flowchart.py` script provides a `Flowchart` class that facilitates the creation, rendering, and saving of a flowchart. It allows users to add elements to a flowchart, connect them with arrows, and label the connections. The flowchart is rendered using the matplotlib library.

##### **Features**

- **Grid System:** Elements are placed on a grid, allowing for organized placement and alignment of flowchart elements.
- **Customizable Size:** Users can specify the number of rows and columns in the grid, the cell size, and the text size for labels.
- **Connection Labels:** Arrows connecting elements can be labeled to indicate the flow of processes.

##### **Methods**

- **`__init__(self, rows, columns, cell_size, text_size)`** - Initializes a new Flowchart object.
- **`grid_to_coords(self, row, col)`** - Converts grid coordinates to x, y coordinates on the plot.
- **`add_element(self, element, row, col)`** - Adds an element to the flowchart at the specified grid position.
- **`connect(self, elem1, elem2, label)`** - Connects two elements with an optional label on the arrow.
- **`draw(self, filename)`** - Draws the complete flowchart and saves it as SVG and PNG files.

##### **Usage Example**

```python
from flowchart import Flowchart
from elements import Process, StartStop 

# Create a flowchart with a 5x5 grid, each cell of size 1.0, and text size 12 
flow = Flowchart(5, 5, 1.0, 12)  

# Add elements 
start = flow.add_element(StartStop("Start"), 1, 2) 
process = flow.add_element(Process("Process"), 2, 2) 
end = flow.add_element(StartStop("End"), 3, 2)  

# Connect elements with labels 
flow.connect(start, process, "Begin")
flow.connect(process, end, "Finish")  # Draw and save the flowchart 
flow.draw("example")```

In this example, a flowchart with a 5x5 grid is created. A start element, a process element, and an end element are added to the flowchart at specific positions on the grid. The elements are then connected with labeled arrows, and the complete flowchart is drawn and saved as `example.svg` and `example.png` files.