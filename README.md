# 🎀 🐈  PINKY PROMISE MOBILE APP  🐈 🎀

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

# ASSIGNMENT 7
### 1. Explain what are stateless widgets and stateful widgets, and explain the difference between them.
Stateless Widgets are static and don't hold mutable state. They will update when external data changes. 

Stateful Widgets are dynamic widgets that maintain a mutable state that can change over time. A widget is called stateful if a widget changes when a user interacts with it.

#### DIFFERENCE BETWEEN STATELESS AND STATEFUL WIDGETS:
##### State Management:
Stateless widgets do not require state management unlike stateful widgets
##### Rendering:
Stateless widgets are only rendered once and update depending on the change of external data. Stateful widgets re-renders when input data changes.
##### Behaviour:
Stateless widgets are static and Stateful widgets are dynamic.


### 2. Mention the widgets that you have used for this project and its uses.
#### MaterialApp:
Top-level widget that provides a default structure for a flutter app, including theme settings and navigation. It's used to initialize the app and apply theme configurations globally.

#### Scaffold: 
Provides the basic visual layout structure for the app. Here, it's used to give the page a default layout structure.

#### AppBar: 
Used as the top section of the screen, which typically contains the title and optional actions. The app title "PINKY PROMISE" is displayed using bold white font by the AppBar.

#### Padding:
Used to add space around the child widgets.

#### Column: 
Arranges its child widgets vertically in a single column. In this app, it's used to stack the rows, the welcome message, and the grid of ItemCard widgets vertically.

#### Row:
Arranges its children horizontally in a single row. Here, it is used to display the InfoCard widgets for "NPM," "Name," and "Class" next to each other.

#### Card:
Used to create a material design card with rounded corners and shadows. It wraps the InfoCard content to give each piece of information a boxed appearance, visually separating them.

#### Container:
A versatile widget that allows for adding padding, margins, background color, and more. Here, it's used to control the layout of the contents within Card and ItemCard widgets.

#### GridView.count:
Creates a grid layout where we can control the number of columns. In this app, it is used to display ItemCard widgets in a 3-column grid.

#### Text:
Used to display text on screen. Here, it's used for showing title, welcome message, and other content within the cards.

#### Icon:
This is used to display the icons from the provided library (Material Icons). The ItemCard uses icons to represent the actions "View Product List", "Logout" and "Add Product".

#### Material:
Provides a canvas for material design styling, including shadows and rounded corners.

#### InkWell:
A gesture detector that shows a ripple effect when tapped. 

#### MediaQuery: 
Used here to access the device's screen dimensions. It's used within InfoCard to adjust the width of the card based on the screen size.

#### SnackBar:
Provides message to the user. In this project, for example, "You have pressed the View Product List button" message will show when the View Product List button is pressed.

### 3. What is the use-case for setState()? Explain the variable that can be affected by setState().
The setState() method is used to update the component's state in response to events, server responses, or changes in props. It queues all the state updates and tells commands to re-render the component and its children with the new state. The variables affected by setState() are those defined within the component's state object.

### 4. Explain the difference between const and final keyword.
A variable declared with the final keyword is initialized at runtime and can be assigned only once. In contrast, a variable with the const keyword is evaluated at compile-time and is already assigned by the time the program is at runtime, meaning the value must be known and fixed during compilation. 

### 5. How I implemented the checklists. 
#### A. Generating a New Flutter Project with the E-Commerce theme that matches the previous assignments.
1. To do this, i generated a new Flutter project in the terminal with the name pinky_promise and entered the directory with these commands.
 ```
flutter create pinky_promise
cd pinky_promise
 ```
2. Then i ran 'flutter run' to run the flutter application. I used Google Chrome to run this. 
3. Then i performed:
```
git init
```
in the root folder and performed add-commit-push to a new github repository titled "pinky-promise-mobile"
4. After generating a new flutter project, I reorganized the project structure with a few steps. First, I created a new file named menu.dart in the pinky_promise/lib directory and added the following code to it
```
import 'package:flutter/material.dart';
```
5. Then I cut these classes from the main.dart file
```
class MyHomePage ... {
    ...
}

class _MyHomePageState ... {
    ...
}
```
6. After that, I imported:
```
import 'package:pinky_promise/menu.dart';
```
to the top of the main.dart file since main.dart no longer understands the MyHomePage class since it is moved to the menu.dart file
7. Then, I changed MaterialApp to this:
```
colorScheme: ColorScheme.fromSwatch(
    primarySwatch: Colors.pink,
).copyWith(secondary: Colors.pink[500]),
```
and changed const MyHomePage(title: 'Flutter Demo Home Page') to become
```
MyHomePage(),
```
8. menu.dart will look like this
```
class MyHomePage extends StatelessWidget {
    MyHomePage({super.key});

    @override
    Widget build(BuildContext context) {
	return Scaffold(
	    ... 
	);
    }
}
```
and main.dart will look like this
```
import 'package:flutter/material.dart';
import 'package:pinky_promise/menu.dart';


void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        // This is the theme of your application.
        //
        // TRY THIS: Try running your application with "flutter run". You'll see
        // the application has a purple toolbar. Then, without quitting the app,
        // try changing the seedColor in the colorScheme below to Colors.green
        // and then invoke "hot reload" (save your changes or press the "hot
        // reload" button in a Flutter-supported IDE, or press "r" if you used
        // the command line to start the app).
        //
        // Notice that the counter didn't reset back to zero; the application
        // state is not lost during the reload. To reset the state, use hot
        // restart instead.
        //
        // This works for code too, not just values: Most code changes can be
        // tested with just a hot reload.
         colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.pink,
          ).copyWith(secondary: Colors.pink[500]),
      ),
      home: MyHomePage(),
    );
  }
}
```
#### B. Create three simple buttons with icons
1. Firstly, I added these in outside the MyHomePage and InfoCard class.
```
 ...
 class ItemHomepage {
     final String name;
     final IconData icon;

     ItemHomepage(this.name, this.icon);
 }
 ...
```

2. Then, I created a list of ItemHomepage that contains the buttons to be added to the MyHomePage class.
```
 class MyHomePage extends StatelessWidget {  
     ...
        final List<ItemHomepage> items = [
            ItemHomepage("View Product List", Icons.list),
            ItemHomepage("Add Product", Icons.add),
            ItemHomepage("Logout", Icons.logout),
        ];
     ...
 }
```
3. Then I created the ItemCard class
```
class ItemCard extends StatelessWidget {
  final ItemHomepage item;

  const ItemCard(this.item, {super.key});

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      borderRadius: BorderRadius.circular(12),
      child: InkWell(
        onTap: () {
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("You have pressed the ${item.name} button!")),
            );
        },
        child: Container(
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```

#### C. Implement different colors for each button (View Product List, Add Product, and Logout).
To do this, i changed the list of ItemHomePage I previously created to the following.
```
 class MyHomePage extends StatelessWidget {  
     ...
        final List<ItemHomepage> items = [
            ItemHomepage("View Product List", Icons.list, Colors.pink.shade100),
            ItemHomepage("Add Product", Icons.add, Colors.pink.shade200),
            ItemHomepage("Logout", Icons.logout, Colors.pink.shade300),
        ];
     ...
 }
```
Then added a 'color' property in ItemHomePage
```
class ItemHomepage {
  final String name;
  final IconData icon;
  final Color color; // Tambahkan properti warna

  ItemHomepage(this.name, this.icon, this.color);
}
```

And used the property 'color' in ItemCard
```
class ItemCard extends StatelessWidget {
  final ItemHomepage item;

  const ItemCard(this.item, {super.key});

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      borderRadius: BorderRadius.circular(12),
      child: InkWell(
        onTap: () {
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("You have pressed the ${item.name} button!")),
            );
        },
        child: Container(
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}

```
#### D. Display a Snackbar with messages.
To do this, I created an ItemCard class to display the buttons (has been done in the previous step). This step will also display snackbar messages. These lines specifically will display the snackbar with messages.
```
...
      child: InkWell(
        onTap: () {
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("You have pressed the ${item.name} button!")),
            );
        },
...
```