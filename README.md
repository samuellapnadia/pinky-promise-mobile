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

<details>
  <summary><strong>ASSIGNMENT 7</strong></summary>
  
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
to the top of the main.dart file since main.dart no longer understands the MyHomePage class since it is moved to the menu.dart file.

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
</details>
<details>
  <summary><strong>ASSIGNMENT 8</strong></summary>

### 1.What is the purpose of const in Flutter? Explain the advantages of using const in Flutter code. When should we use const, and when should it not be used?
The const keyword is used when the value of the variable is known at compile-time and never changes. The purpose of it is to inform Dart that certain values are known at compile-time, which makes apps more memory-efficient and faster. Using const widgets allows Flutter to reuse the same instance wherever that widget is used in the widget tree, reducing memory usage. 

We should use const when a widget's properties do not change. 
We should not use const when a widget's properties need to change, such as a widget with an animation or one that responds to user interactions. We also shouldn't use const when values are not known at compile-time.

### 2. Explain and compare the usage of Column and Row in Flutter. Provide example implementations of each layout widget!

Column and Row are used by adding a list of children widgets to the Row/Column widget.
The differences between the two are:

Column: aligns child widgets in a vertical direction
Row: align child widgets along a horizontal line.

Example implementation:
Column:
```
Center(
  child: Column(
    children: [
      const Padding(
        padding: EdgeInsets.only(top: 16.0),
        child: Text(
          'Hi MofuBuddy! Welcome back to Pinky Promise!',
          style: TextStyle(
            fontWeight: FontWeight.bold,
            fontSize: 18.0,
          ),
        ),
      ),
      GridView.count(
        primary: true,
        padding: const EdgeInsets.all(20),
        crossAxisSpacing: 10,
        mainAxisSpacing: 10,
        crossAxisCount: 3,
        shrinkWrap: true,
        children: items.map((ItemHomepage item) {
          return ItemCard(item);
        }).toList(),
      ),
    ],
  ),
)

```

Row:
```
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    InfoCard(title: 'NPM', content: npm),
    InfoCard(title: 'Name', content: name),
    InfoCard(title: 'Class', content: className),
    ],
  ),

```
### 3. List the input elements you used on the form page in this assignment. Are there other Flutter input elements you didn't use in this assignment? Explain!

Input elements I used on the form page:
- TextFormField: used to capture text input for Product and Description
- ElevatedButton: this button is used to submit the form and save the product data. 

Other Flutter input elements you didn't use in this assignment
- Checkbox: useful for capturing binary choices.
- Radio: useful for selecting one option from a list of mutually exclusive choices.
- Switch: ideal for toggling a setting on or off. Often used in preference forms
- Slider: used for selecting a value from a continuous range.
- DatePicker:  used to let users select dates.
- DropdownButton: allows users to select from a list of options.
- AutoComplete: provides a text field with auto-completion capabilities.

### 4. How do you set the theme within a Flutter application to ensure consistency? Did you implement a theme in your application?
To ensure consistency, I used MaterialApp in the the main.dart file:
```
import 'package:flutter/material.dart';
import 'package:pinky_promise/screens/menu.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        // Define a consistent color scheme for the app
        colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.pink,
        ).copyWith(
          secondary: Colors.pink[500], 
        ),
      ),
      home: MyHomePage(),
    );
  }
}

```
Regarding theme implementation, I implemented a "Pink" theme for this application, similar to what I did in the previous assignments with flutter. 
- Primary Swatch: i used
```
primarySwatch: Colors.pink
```
which sets the primary color of your app to shades of pink. This color is automatically applied to elements like the AppBar background, buttons, and any widget that uses Theme.of(context).colorScheme.primary.
- Secondary Color: The secondary color here is 
```
secondary: Colors.pink[500]
```
- AppBar Styling: by setting colorScheme.primary to pink, the AppBar inherits the pink color as its background color, which ensures consistency.

### 5.  How do you manage navigation in a multi-page Flutter application?
To manage navugation in a multi-page Flutter application, first I used Navigator.pushReplacement to navigate between screens when specific buttons are pressed. 
Example:
```
ListTile(
  leading: const Icon(Icons.home_outlined),
  title: const Text('Home Page'),
  onTap: () {
    Navigator.pushReplacement(
      context,
      MaterialPageRoute(builder: (context) => MyHomePage()),
    );
  },
),

```

I also used Drawer widget to create a side navigation menu for the app.

```
drawer: const LeftDrawer(),

```

```
Drawer(
  child: ListView(
    children: [
      DrawerHeader(
        decoration: BoxDecoration(
          color: Theme.of(context).colorScheme.primary,
        ),
        child: const Column(
          children: [
            Text(
              'Pinky Promise',
              style: TextStyle(
                fontSize: 24,
                fontWeight: FontWeight.bold,
                color: Colors.white,
              ),
            ),
          ],
        ),
      ),
      ListTile(
        leading: const Icon(Icons.add),
        title: const Text('Add Product'),
        onTap: () {
          Navigator.pushReplacement(
            context,
            MaterialPageRoute(builder: (context) => ProductEntryFormPage()),
          );
        },
      ),
    ],
  ),
);

```

### HOW I IMPLEMENTED THE CHECKLISTS
#### A. Creating at least one new page in the application, specifically a form page to add a new item.
1. To do this, I created two new directory in lib, namely screens and widgets. But I used lib/screens in this step.
2. I moved menu.dart to this directory and added a new file named productentry_form.dart with the code inside of the file as follows:
```
import 'package:flutter/material.dart';
import 'package:pinky_promise/widgets/left_drawer.dart';

class ProductEntryFormPage extends StatefulWidget {
  const ProductEntryFormPage({super.key});

  @override
  State<ProductEntryFormPage> createState() => _ProductEntryFormPageState();
}

class _ProductEntryFormPageState extends State<ProductEntryFormPage> {
  final _formKey = GlobalKey<FormState>();
  String _product = "";
  String _description = "";
  int _amount = 0;
  int _coquetteness = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Center(
          child: Text(
            'Add Your Product!',
          ),
        ),
        backgroundColor: Theme.of(context).colorScheme.primary,
        foregroundColor: Colors.white,
      ),
      drawer: const LeftDrawer(),
      body: Form(
        key: _formKey,
        child: SingleChildScrollView(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Product",
                    labelText: "Product",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  onChanged: (String? value) {
                    setState(() {
                      _product = value!;
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "Product cannot be empty!";
                    }
                    return null;
                  },
                ),
              ),
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Description",
                    labelText: "Description",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  onChanged: (String? value) {
                    setState(() {
                      _description = value!;
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "Description cannot be empty!";
                    }
                    return null;
                  },
                ),
              ),
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Amount",
                    labelText: "Amount",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  keyboardType: TextInputType.number,
                  onChanged: (String? value) {
                    setState(() {
                      _amount = int.tryParse(value!) ?? 0;
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "Amount cannot be empty!";
                    }
                    if (int.tryParse(value) == null) {
                      return "Amount must be a number!";
                    }
                    return null;
                  },
                ),
              ),
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Coquetteness",
                    labelText: "Coquetteness",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  keyboardType: TextInputType.number,
                  onChanged: (String? value) {
                    setState(() {
                      _coquetteness = int.tryParse(value!) ?? 0; // Corrected here
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "Coquetteness cannot be empty!";
                    }
                    if (int.tryParse(value) == null) {
                      return "Coquetteness must be a number!";
                    }
                    return null;
                  },
                ),
              ),
              Align(
                alignment: Alignment.bottomCenter,
                child: Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: ElevatedButton(
                    style: ButtonStyle(
                      backgroundColor: MaterialStateProperty.all(
                        Theme.of(context).colorScheme.primary,
                      ),
                    ),
                    onPressed: () {
                      if (_formKey.currentState!.validate()) {
                        showDialog(
                          context: context,
                          builder: (context) {
                            return AlertDialog(
                              title: const Text('Product successfully saved, buddy!!'),
                              content: SingleChildScrollView(
                                child: Column(
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  children: [
                                    Text('Product: $_product'),
                                    Text('Description: $_description'),
                                    Text('Amount: $_amount'),
                                    Text('Coquetteness: $_coquetteness'),
                                  ],
                                ),
                              ),
                              actions: [
                                TextButton(
                                  child: const Text('OK'),
                                  onPressed: () {
                                    Navigator.pop(context);
                                    _formKey.currentState!.reset();
                                    setState(() {
                                      _product = "";
                                      _description = "";
                                      _amount = 0;
                                      _coquetteness = 0;
                                    });
                                  },
                                ),
                              ],
                            );
                          },
                        );
                      }
                    },
                    child: const Text(
                      "Save",
                      style: TextStyle(color: Colors.white),
                    ),
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}

```
I have included four input elements, namely Product, Description, Price, and Coquetteness, with the input field not allowed to be empty, and each input field have contain data in the model's data type. A save button is also included. 

#### B. Redirect the user to the new item addition form when they press the Add Item button on the main page.
1. To do this, I created product_card.dart in widgets directory with the content as follows:
```
import 'package:pinky_promise/screens/productentry_form.dart';
import 'package:flutter/material.dart';

class ItemHomepage {
  final String name;
  final IconData icon;
  final Color color;

  ItemHomepage(this.name, this.icon, this.color);
}

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
          if (item.name == "Add Item") {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => const ProductEntryFormPage()),
            );
          } else {
            ScaffoldMessenger.of(context).showSnackBar(
              SnackBar(content: Text("You have pressed the ${item.name} button!")),
            );
          }
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
                const SizedBox(height: 5),
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
Here, I updated the onTap Handler to navigate to ProductEntryFormPage. ItemHomePage and ItemCard were taken previously from menu.dart
 
#### C. Display the data from the form in a pop-up after pressing the Save button on the new item addition form page.
To do this, I modified the productentry_form.dart file. I create a button as the next child of Column and wrap the button with Padding and Align. 
```
Align(
  alignment: Alignment.bottomCenter,
  child: Padding(
    padding: const EdgeInsets.all(8.0),
    child: ElevatedButton(
      style: ButtonStyle(
        backgroundColor: MaterialStateProperty.all(
          Theme.of(context).colorScheme.primary,
        ),
      ),
      onPressed: () {
        if (_formKey.currentState!.validate()) {
          showDialog(
            context: context,
            builder: (context) {
              return AlertDialog(
                title: const Text('Product successfully saved, buddy!!'),
                content: SingleChildScrollView(
                  child: Column(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      Text('Product: $_product'),
                      Text('Description: $_description'),
                      Text('Price: $_price'),
                      Text('Coquetteness: $_coquetteness'),
                    ],
                  ),
                ),
                actions: [
                  TextButton(
                    child: const Text('OK'),
                    onPressed: () {
                      Navigator.pop(context); // Closes the dialog
                      _formKey.currentState!.reset(); // Resets the form
                      setState(() {
                        _product = "";
                        _description = "";
                        _price = 0;
                        _coquetteness = 0;
                      });
                    },
                  ),
                ],
              );
            },
          );
        }
      },
      child: const Text(
        "Save",
        style: TextStyle(color: Colors.white),
      ),
    ),
  ),
);
```
#### D. Create a drawer in the application
I implemented this step by making a left_drawer.dart file in the lib/widgets directory with the content as follows:
```
import 'package:flutter/material.dart';
import 'package:pinky_promise/screens/menu.dart';
import 'package:pinky_promise/screens/productentry_form.dart';

class LeftDrawer extends StatelessWidget {
  const LeftDrawer({super.key});

  @override
  Widget build(BuildContext context) {
    return Drawer(
      child: ListView(
        children: [
          DrawerHeader(
            decoration: BoxDecoration(
              color: Theme.of(context).colorScheme.primary,
            ),
            child: const Column(
              children: [
                Text(
                  'PINKY PROMISE',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 24,
                    fontWeight: FontWeight.bold,
                    color: Colors.white,
                  ),
                ),
                Padding(padding: EdgeInsets.all(8)),
                Text(
                  "Your favorite coquette trinket shop!",
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    color: Colors.white,
                    fontWeight: FontWeight.normal,
                    fontSize: 15.0,
                  ),
                ),
              ],
            ),
          ),
          ListTile(
            leading: const Icon(Icons.home_outlined),
            title: const Text('Home Page'),
            onTap: () {
              Navigator.pushReplacement(
                context,
                MaterialPageRoute(
                  builder: (context) => MyHomePage(),
                ),
              );
            },
          ),
          ListTile(
            leading: const Icon(Icons.add),
            title: const Text('Add Item'),
            onTap: () {
              Navigator.pushReplacement(
                context,
                MaterialPageRoute(
                  builder: (context) => ProductEntryFormPage(),
                ),
              );
            },
          ),
          ListTile(
            leading: const Icon(Icons.logout),
            title: const Text('Logout'),
            onTap: () {
              // logout logic here 
              Navigator.pop(context);
            },
          ),
        ],
      ),
    );
  }
}

```
In the left_drawer.dart file, contained Home, Logout and Add Item. But only Home & Add Item have been implememented here. Home option can redirect the user to the main page and the Add Item redirects the user to the new item addition form page.