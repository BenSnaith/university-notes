## Introduction

- So far, our applications have only used text or drawn on a canvas, for simplicity
- This has allowed us to focus on the fundamental issues in developing object-oriented software
- Graphical User Interfaces (GUIs) are also constructed from interacting objects, but they have a specialised structure. In addition, creating a GUI with a reasonable design requires some more advanced language features.

## Java GUI Libraries

Abstract Windowing Toolkit (AWT)

- Available since 1.0, uses native GUI components
- Java 1.1 introduced options for the “Java look and feel”
- Very outdated — for a native look, use IBM SWT (Eclipse)

Swing

- Since Java 1.2: look and feel is entirely OS-independent
- More modern in design and capabilities than AWT
- However, it is outdates in looks and design as well

JavaFX

- Bundled with Java 8+
- Supports 3D graphics, video, stylesheets, and webviews
- Instead of writing Java code, we can load FXML files

## Software Requirements

Required Java Development Kit (JDK)

- You should already have JDK 11 or newer
- An IDE
- JavaFX Scene Builder 2.0: Visual Editor for FXML files

## Three main aspects of GUI construction

Components

- Basic building blocks: buttons, labels, text fields
- We can customise through setters and stylesheets

Interface construction: arranging components

- We place components inside containers
- Containers have layout managers to place/size components (e.g. in rows, columns, grids…)
- Containers can be nested within other containers

Event handling: reacting to user input

- We can attach listener objects to components
- We can delegate on a controller

## Example app: Hello Name!

- First, we will do it by writing Java code. This is cumbersome but powerful: we can change components based on inputs
- For fixed UIs, FXML files are far more comfortable
- For UIs with fixed and dynamic parts, we can do the fixed part with FXML and then do the dynamic part with the code.

## JavaFX Launcher Class

```Java
public class Main extends Application {
	@Override
	public void start(Stage primaryStage {
		// set up the GUI here
	}

	public static void main(String[] args) {
		launch(args);
	}
}
```

- All the GUI setup code should go into `start(Stage)`
- The Stage is the window: it can change between Scenes

## Main container: GridPane

```Java
@Override
public void start(Stage primaryStage) {
	GridPane root = new GridPane();
	root.setAlignment(Pos.CENTER);
	root.setHgap(5.0);
	root.setVgap(5.0);
	root.setPadding(new Insets(10));

	/* ... */
}
```

- We need a root container for all our components: GridPane is a specific one that lays them out in a grid of cells
- We also set some properties: horizontal and vertical gaps of 5 units between cells, and padding of 10 units

## Name entry: TextField

```Java
@Override
public void start(Stage primaryStage) {
	/* ... */	
	TextField textName = new TextField();
	textName.setPromptText("Enter your name:");
	textName.setMaxWidth(Double.MAX_VALUE);
	textName.setMinWidth(160);
	GridPane.setHgrow(textName, Priority.ALWAYS);
	root.add(textName, 0, 0);
	/* ... */
}
```

- TextField allows entering a single line of text
- We change some properties and provide desired min/max width, for GridPane to take into account
- Finally, we add it to the grid column at column 0, row 0

## Confirmation: Button

```Java
@Override
public void start(Stage primaryStage) {
	/* ... */
	final Button btnConfirm = new Button();
	btnConfirm.setMinWidth(70);
	btnConfirm.setText("Confirm");
	root.add(btnConfirm, 1, 0);
	/* ... */
}
```

- We add the “Confirm” button here, with some dimensions
- We add it to the grid at column 1, row 0
- It doesn’t do anything yet — we’ll look at that later

## Setting up the scene

```Java
@Override
public void start(Stage primaryStage) {
	/* ... */
	Scene scene = new Scene(root, 300, 50);
	primaryStage.setTitle("Example Collection");
	primaryStage.setScene(scene);
	primaryStage.show();
}
```

- We create a 300x50 pixels Scene with the GridPane
- We change the title and switch the scene in the Stage: this tells the GridPane to compute the exact dimensions and positions of all the components
- We finally show the Stage (i.e. window) to the user

## Alternate Approach: FXML

```Java
@Override
public void start(Stage primaryStage) {
	try {
		final FXMLLoader l = new FXMLLoader();
		l.setLocation(getClass().getResource("HelloName.fxml"));
		GridPane root = (GridPane) l.load();

		Scene scene = new Scene(root, 300, 50);
		/* ... */
	}
	catch(IOException e) {
		e.printStackTrace();
	}
}
```

- Doing UIs with code is repetitive and cumbersome
- Instead, we can load an .fxml file from the Scene Builder
- .fxml must end up in the same folder as the .class file

## Contents of the FXML file

```Java
<?xml version="1.0" encoding
insert the code

THERE IS ALOT OF CODE PLEASE COPY AND PASTE IT IS HUGE PLEASE INSERT HEHEHE
```

## Why use FXML?

Good support for visual editing?

- You can see how the UI will look like on the fly
- The Scene Builder can be used by UI/UX designers

Loading files is easier than generating Java code

- There have been visual editors for Swing UIs, which locked part of your code in place — you’d better not touch it!
- FXML is much simpler and more reliable
- Same approach: GTK Glade, Qt QML, Android UIs

Underlying principles

- FXML is a domain-specific language for JavaFX UIs
- Our second program works in a data-driven way, by loading files rather than coding everything (common in games)

## Adding behaviour into our program

GUIs are event-driven

- JavaFX runs an event loop in the background, checking if the user has done anything
- When the user does something, it triggers that event handlers that we have registered, we will do that now

JavaFX event handlers

- They typically implement the `EventHandler<T>` interface
- handle(`ActionEvent`) takes the event and does something
- Event objects provide additional information: e.g. `getSource()` in `ActionEvent` tells you the component that it came from

## Event handlers for code-based UI

```Java
final Button btnConfirm = new Button();
/* ... */
btnConfirm.setOnAction(new EventHandler<ActionEvent>() {
	@Override
	public void handle(ActionEvent event) {
		Alert alert = new Alert(AlertType.INFORMATION);
		alert.setTitle("Hello There!");
		alert.setContentText("Hello " + textName.getText() + "!");
		alert.showAndWait();
});
```

- The above syntax defines an anonymous class, implements in EventHandler, and creates and instance of it
- The basic syntax is new `Supertype() { classbody }` where Supertype is the name of the base interface/class
- We set it to be invoked whenever the button is pressed

```Java
final Button btnConfirm = new Button();
/* ... */
btnConfirm.setOnAction(event -> {
		Alert alert = new Alert(AlertType.INFORMATION);
		alert.setTitle("Hello There!");
		alert.setContentText("Hello " + textName.getText() + "!");
		alert.showAndWait();
});
```

- You can make it even shorter using the Java 9+ lambda notation, which is useful when you need to pass an object implementing an interface with only one method (a Functional Interface)
- For `EventHandler`, it is just `event -> { code }`
- Same anonymous class as before: compiler fills in the details

## Event Handlers for FXML-based UI

Concerns

- We don’t create the TextField or the Button ourselves
- How do we access them?
- How do we associate the event handler to the button?

General Approach

- We need to create the controller class
- The FXML file is extended with component IDs and the names of the controller methods to run
- The FXML loading code is told to use the Controller
- Controller will have a filed for the TextField, and a method to react to the button being pressed

```Java
<?xml version="1.0" encoding="UTF-8"?>
...
<GridPane ... xmlns:fx="http://javafx.com/fxml/1">
<children>
	<Button ... onAction="\#confirmPressed" />
	<TextField fx:id="textName" ... />
</children>
...
</GridPane>
```

- “onAction” tells JavaFX to invoke “confirmPressed()” or “confirmPressed(ActionEvent)” when the button is pressed
- “fx:id” tells JavaFX to set “textName” on the contoller class to the TextField used in the form

```Java
public class HelloNameController {
	@FXML TextField textName;
	
	@FXML public void confirmPressed() {
		Alert alert = new Alert(AlertType.INFORMATION);
		alert.setTitle("Hello There!");
		alert.setContentText("Hello " + textName.getText() + "!");
		alert.showAndWait();
	}
}
```

- JavaFX uses the elements annotated with “@FXML”
- JavaFX sets the “textName” when loading the UI
- JavaFX invokes “confirmPressed” when button is pressed

```Java
@Override
public void start(Stage primaryStage) {
	try {
		final FXMLLoader l = new FXMLLoader();
		l.setLocation(getClass().getResource("HelloName.fxml"));
		GridPane root = (GridPane) l.load();

		Scene scene = new Scene(root, 300, 50);
		/* ... */
	}
	catch(IOException e) {
		e.printStackTrace();
	}
}
```

- Pass an instance of out controller class to setController
- Then we can load as usual: JavaFX will fill in the fields of the controller and set up the event listeners for us

## Further advantages of an FXML-based UI

- In addition to visual editing, using FXML enforces a strong separation between the “view” of your program (your GUI) and the “controller” that reacts to the inputs
- We could completely rearrange/restyle the UI and still have the same controller, as long as we have that TextField with the same “fx:id” somewhere
- In the next lecture, we will also consider how to separate the “model” of your program (the core functionality which is unrelated to the UI) from the “view” and the “controller”

## Working with components

Accessor (getter) and mutator (setter) methods

- TextField: `getText()` / `setText()`
- ComboBox, ChoiceBox: `getValue()` / `setValue()`
- ListView: `getSelectionModel()`
- ToggleButton, CheckBox, RadioButton: `isSelected()` / `getSelected()`
- … and many others — check the Javadocs!

Properties

- A property encapsulates a value so we can watch it change
- For instance, `textProperty()` in TextField returns a StringProperty with the text of the field at any time
- We will discuss this later — they are very powerful!

## Revisiting Containers

Why Containers?

- Very old GUI frameworks required manual placement
- However, screens come in all sizes and shapes now!
- It is also rather fiddly to get all the dimensions right
- We would rather have the computer do the math

Basic concepts

1. We add containers and components to a container
2. We define desired dimensions
3. We add layout data to the components
4. When the Stage is switched to out new Scene, the containers will computer the placements and the sizes

## VBox and HBox

IMAGE

- VBox places all elements in a single column, vertically
- HBox places all elements in a single row, horizontally
- VBox is a simple way to have a MenuBar at the top, then something else below

## BorderPane

IMAGE

- Elements can be placed on the borders, or at the center
- Top/Bottom are useful for menu bar / status bar

## StackPane

IMAGE

- Elements are placed one on top of the other, centered

## AnchorPane

IMAGE

- Layout is based on distances between edges
- Here we have a button that has top, left and right edges 20 pixels away from the edges of the AnchorPane

## GridPane

- Elements are placed in rows and columns
- Elements can span more than one row and or column
- Set through the “Layout” section in the JavaFX Scene Builder, or by using “add(…)” in the GridPane

## TitledPane

- Has a nice softly shaped title
- Optionally collapsible
- Expects another container inside (e.g. an AnchorPane)

## Combining containers: answer

- BorderPane outside: with Menu at the TOP, Label at the BOTTOM and GridPane at the CENTER
- GridPane: Label in (0, 0), VBox in (0, 1) and Pane in (1, 1)
- VBox has the two buttons, with margains between them

## Keeping GUI and data model in sync

- Suppose we want to add behaviour to this GUI
- We link this FXML to a controller… and then what…

## First approach: event handlers

```Java
public class ListenerController {
	@FXML Label labelResult;
	@FXML TextField textOperand;
	private int value = 0;

	@Override @FXML public void addPressed() {
		try {
			int operand = Integer.valueOf(textOperand.getText();
			value += operand;
			labelResult.setText("Result: " + value);
		}
		catch(NumberFormatException e) {
			e.printStackTrace();
		}
	}
}
```

## Second approach: applying DRY

```Java
public class ListenerRefactoredController 
		extends AbstractCalculatorController {
	private int value = 0;

	@Override
	public void addPressed() {
		Integer operand = getOperand();
		if (operand != null) {
			value += operand;
			updateLabel();
		}
	}
	...
}
```

## Third approach: using properties

```Java
public class PropertyController extends AbstractCalculatorController {
	private IntegerProperty value = new SimpleIntegerProperty(0);
	@FXML public void initialize() {
		value.addListener((property, oldValue, newValue) -> {
			labelResult.setText(”Result: ” + newValue);
		});
	}
	@Override
	public void addPressed() {
	Integer operand = getOperand();
		if (operand != null) {
			value.set(value.get() + operand);
		}
	}
...
}
```

- A property is a value that we can get, set and watch
- Pressed() methods simply update property
- Listener reacts by updating the label
- Listener registered from FXML “initialize” method

## More on properties

![[Untitled 46.png|Untitled 46.png]]

- Most JavaFX UI components have `xProperty()` methods
- Properties implements the `ObservableValue<T>` interface
- We can also create out own, custom UI components or for exposing changes in our data model

## Why properties?

- We can have our data model (or just “model”) notify the UI that is has changed, and allow the UI to refresh itself
- This way, we separate two concerns:
    - Updating the data model from the controller
    - Updating the view to show the new data model
- This can implement a Model-View-Controller architecture
    - Model exposes its information through properties
    - View listens to properties and updates itself
    - Controller updated the model