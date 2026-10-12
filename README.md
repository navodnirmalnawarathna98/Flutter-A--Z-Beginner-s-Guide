# Flutter A--Z: Beginner's Guide

> **From a clean `main.dart` to a multi-page Flutter app**\
> A step-by-step classroom guide for learning Flutter and Dart using
> Android Studio.

This guide is designed for students who are new to Flutter. You
will start with a simple working app, learn what each important line
does, organise code into separate files and folders, navigate between
pages, pass data, and build basic interactive features.

## Table of Contents

-   [Learning Outcomes](#learning-outcomes)
-   [1. What Is Flutter?](#1-what-is-flutter)
-   [2. Understand the Flutter
    Project](#2-understand-the-flutter-project)
-   [3. Clean `main.dart` and Start from
    Zero](#3-clean-maindart-and-start-from-zero)
-   [4. Understand the Main Flutter
    Concepts](#4-understand-the-main-flutter-concepts)
-   [5. Build the First Screen](#5-build-the-first-screen)
-   [6. Learn Basic UI Widgets](#6-learn-basic-ui-widgets)
-   [7. Understand Stateless and Stateful
    Widgets](#7-understand-stateless-and-stateful-widgets)
-   [8. Organise Code into Files and
    Folders](#8-organise-code-into-files-and-folders)
-   [9. Create a Separate Home Screen](#9-create-a-separate-home-screen)
-   [10. Create More Pages](#10-create-more-pages)
-   [11. Navigate Between Pages](#11-navigate-between-pages)
-   [12. Pass Data Between Pages](#12-pass-data-between-pages)
-   [13. Create Reusable Widgets](#13-create-reusable-widgets)
-   [14. Build a Counter Screen](#14-build-a-counter-screen)
-   [15. Build a Student Registration
    Form](#15-build-a-student-registration-form)
-   [16. Named Routes](#16-named-routes)
-   [17. Imports and Common Errors](#17-imports-and-common-errors)
-   [18. Final Project Structure](#18-final-project-structure)
-   [19. Grade 11 Mini Project](#19-grade-11-mini-project)
-   [20. Suggested Teaching Plan](#20-suggested-teaching-plan)
-   [21. Student Practice Activities](#21-student-practice-activities)
-   [22. Assessment Rubric](#22-assessment-rubric)
-   [23. Final Tips](#23-final-tips)

------------------------------------------------------------------------

## Learning Outcomes

By the end of this guide, students should be able to:

-   Explain the purpose of `main.dart`, `main()`, `runApp()` and
    `MaterialApp`.
-   Create a basic Flutter screen using common widgets.
-   Understand the relationship between classes, widgets and the widget
    tree.
-   Create folders and Dart files in Android Studio.
-   Import a widget from another file.
-   Navigate between screens and return to a previous screen.
-   Pass a value, such as a student's name, to another screen.
-   Explain the difference between `StatelessWidget` and
    `StatefulWidget`.
-   Use `setState()` for simple UI updates.
-   Read text input and perform basic validation.
-   Build a small multi-page school application.

## 1. What Is Flutter?

Flutter is a framework used to build user interfaces for mobile, web and
desktop applications from a shared codebase. Flutter apps are commonly
written in the Dart programming language.

Think of a mobile app as a house:

-   **Flutter** is the construction system.
-   **Dart** is the language used to give instructions.
-   **Widgets** are the building blocks.
-   **Screens** are the rooms or pages.
-   **Navigation** lets users move between pages.

## 2. Understand the Flutter Project

When you create a Flutter project in Android Studio, you will see
folders and files similar to these:

``` text
my_first_app/
├── android/             # Android platform configuration
├── ios/                 # iOS platform configuration
├── lib/                 # Main Dart application code
│   └── main.dart        # Default entry-point file
├── test/                # Automated tests
└── pubspec.yaml         # Project settings, dependencies and assets
```

For this lesson, most of your work will happen inside `lib/`.

> **Important:** Do not delete the entire project or its configuration
> files. Keep `android/`, `ios/`, `pubspec.yaml` and other generated
> files. We are replacing the starter Dart code, not rebuilding the
> Flutter project from scratch.

### Open the starter file

1.  Open your Flutter project in Android Studio.
2.  Find the `lib` folder.
3.  Open `main.dart`.
4.  Select the starter code and replace it with the examples below.
5.  Run the app on an emulator or connected Android device.

## 3. Clean `main.dart` and Start from Zero

We will build the app in small steps. Type each step, run it where
appropriate, and discuss what each line does.

### Step 1: Import Flutter's Material library

``` dart
import 'package:flutter/material.dart';
```

**What does this mean?**

-   `import` makes code from another library available in this file.
-   `package:flutter/material.dart` provides Material Design widgets
    such as `Text`, `Scaffold`, `AppBar`, buttons and layout widgets.

A classroom analogy: an import is like bringing the correct toolbox
before starting a practical activity.

### Step 2: Create the `main()` function

``` dart
import 'package:flutter/material.dart';

void main() {

}
```

  Code       Simple explanation
  ---------- ------------------------------------------
  `void`     This function does not return a value.
  `main()`   The starting function of a Dart program.
  `{ }`      The body of the function.
  `;`        Ends a Dart statement.

### Step 3: Display your first screen

Replace the contents of `main.dart` with:

``` dart
import 'package:flutter/material.dart';

void main() {
  runApp(
    const MaterialApp(
      home: Scaffold(
        body: Center(
          child: Text('Hello Grade 11!'),
        ),
      ),
    ),
  );
}
```

Run the app. You should see **Hello Grade 11!** in the centre of the
screen.

### Understand the execution flow

``` text
main()
  └── runApp()
       └── MaterialApp
            └── Scaffold
                 └── Center
                      └── Text
```

-   `main()` is where Dart starts.
-   `runApp()` starts the Flutter UI with the root widget.
-   `MaterialApp` sets up a Material-style application.
-   `Scaffold` provides a standard screen structure.
-   `Center` centres its child.
-   `Text` displays a message.

A widget can contain other widgets. The parent-child structure is called
the **widget tree**.

## 4. Understand the Main Flutter Concepts

Now place the app inside a class. This is a common structure for Flutter
projects.

### Step 4: Create `MyApp`

Replace `main.dart` with:

``` dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        body: Center(
          child: Text('Hello Grade 11!'),
        ),
      ),
    );
  }
}
```

### Line-by-line explanation

  --------------------------------------------------------------------------
  Code                                   Meaning
  -------------------------------------- -----------------------------------
  `class MyApp`                          Defines a class named `MyApp`.

  `extends StatelessWidget`              Makes this class a widget that does
                                         not manage changing internal state.

  `const MyApp({super.key})`             Defines a constructor for the
                                         widget.

  `@override`                            Indicates that an inherited method
                                         is being implemented.

  `Widget build(BuildContext context)`   Describes the widget UI Flutter
                                         should display.

  `return`                               Returns the widget tree to display.

  `debugShowCheckedModeBanner: false`    Hides the debug banner in the
                                         corner.
  --------------------------------------------------------------------------

### What is a widget?

A widget is a building block of a Flutter user interface.

  Widget             Purpose
  ------------------ -----------------------------------------------------
  `Text`             Displays text.
  `Container`        Can add dimensions, padding, colour and decoration.
  `Column`           Arranges children vertically.
  `Row`              Arranges children horizontally.
  `Center`           Centres its child.
  `Padding`          Adds space around a child.
  `SizedBox`         Adds a fixed gap or constrains width/height.
  `Scaffold`         Provides a standard page layout.
  `AppBar`           Creates a top application bar.
  `ElevatedButton`   Creates a button with a raised visual style.

## 5. Build the First Screen

### Step 5: Add an AppBar and body

``` dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          title: const Text('My First App'),
          backgroundColor: Colors.blue,
          foregroundColor: Colors.white,
        ),
        body: const Center(
          child: Text('Welcome to Flutter!'),
        ),
      ),
    );
  }
}
```

Explain the two main areas:

-   `appBar`: the top section that can contain a title and actions.
-   `body`: the main content area of the page.

### Step 6: Display multiple widgets with `Column`

Replace the `body` with:

``` dart
body: const Center(
  child: Column(
    mainAxisAlignment: MainAxisAlignment.center,
    children: [
      Text('Welcome to Flutter!'),
      SizedBox(height: 20),
      Text('We are learning Dart.'),
      SizedBox(height: 20),
      Text('This is our first application.'),
    ],
  ),
),
```

-   `children` is a list of widgets.
-   `Column` arranges its children vertically.
-   `mainAxisAlignment` controls the arrangement along the main axis.
-   `SizedBox(height: 20)` adds vertical space.

**Class activity:** Change the three text messages and observe the
result.

## 6. Learn Basic UI Widgets

Try these small examples inside a `Column` or `Scaffold` body.

### Text

``` dart
const Text(
  'Welcome to our school app',
  style: TextStyle(
    fontSize: 24,
    fontWeight: FontWeight.bold,
  ),
)
```

### Container

``` dart
Container(
  padding: const EdgeInsets.all(16),
  color: Colors.lightBlue,
  child: const Text('A coloured container'),
)
```

### Row

``` dart
const Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    Icon(Icons.home),
    Icon(Icons.school),
    Icon(Icons.person),
  ],
)
```

### Button

A button can perform an action when pressed:

``` dart
ElevatedButton(
  onPressed: () {
    // Add the action here.
  },
  child: const Text('Press Me'),
)
```

For example, show a message when the button is pressed:

``` dart
ElevatedButton(
  onPressed: () {
    debugPrint('The button was pressed');
  },
  child: const Text('Press Me'),
)
```

`debugPrint()` writes a message to the debug console. It does not
display the message on the app screen.

## 7. Understand Stateless and Stateful Widgets

### `StatelessWidget`

Use it for a widget that does not manage changing internal state, such
as a title or a static information card.

``` dart
class WelcomeMessage extends StatelessWidget {
  const WelcomeMessage({super.key});

  @override
  Widget build(BuildContext context) {
    return const Text('Welcome to Flutter!');
  }
}
```

### `StatefulWidget`

Use it when the interface needs to reflect changing state, such as a
counter or a toggle.

The next example uses `setState()` to tell Flutter to rebuild the
relevant UI after the counter changes.

## 8. Organise Code into Files and Folders

As an app grows, putting every screen into `main.dart` becomes difficult
to maintain. We can separate the code by purpose.

### Create folders in Android Studio

1.  Right-click `lib`.
2.  Choose **New → Directory**.
3.  Create a folder named `screens`.
4.  Repeat to create `widgets`.
5.  Right-click `screens`.
6.  Choose **New → Dart File**.
7.  Create `home_screen.dart`.

### What belongs in each folder?

  -----------------------------------------------------------------------
  File or folder          Responsibility          Example
  ----------------------- ----------------------- -----------------------
  `main.dart`             Starts the app and      `runApp()`
                          configures the app      

  `screens/`              Contains full pages     Home, Students, About

  `widgets/`              Contains reusable UI    Welcome card, custom
                          parts                   button

  `models/`               Contains data classes   Student information
  -----------------------------------------------------------------------

You do not need every folder for every project. Start small and add
folders when they help organise the code.

### Example structure

``` text
lib/
├── main.dart
├── screens/
│   ├── home_screen.dart
│   ├── student_screen.dart
│   ├── student_details_screen.dart
│   ├── about_screen.dart
│   ├── counter_screen.dart
│   └── registration_screen.dart
└── widgets/
    └── welcome_card.dart
```

## 9. Create a Separate Home Screen

Create `lib/screens/home_screen.dart`:

``` dart
import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('School App'),
      ),
      body: const Center(
        child: Text(
          'Welcome to the School App!',
          style: TextStyle(fontSize: 22),
        ),
      ),
    );
  }
}
```

Now update `lib/main.dart`:

``` dart
import 'package:flutter/material.dart';
import 'screens/home_screen.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'School App',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(
          seedColor: Colors.blue,
        ),
        useMaterial3: true,
      ),
      home: const HomeScreen(),
    );
  }
}
```

### Understand the import

``` dart
import 'screens/home_screen.dart';
```

This lets `main.dart` use the `HomeScreen` class declared in
`screens/home_screen.dart`.

The application still starts in `main()`, but the page's UI is now
maintained in a separate file.

> **Try this:** Temporarily remove the import and inspect the error.
> Restore the import and run the app again.

## 10. Create More Pages

We will create three pages: Home, Students and About.

### Create `lib/screens/student_screen.dart`

``` dart
import 'package:flutter/material.dart';

class StudentScreen extends StatelessWidget {
  const StudentScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Students'),
      ),
      body: const Center(
        child: Text(
          'Student List Page',
          style: TextStyle(fontSize: 22),
        ),
      ),
    );
  }
}
```

### Create `lib/screens/about_screen.dart`

``` dart
import 'package:flutter/material.dart';

class AboutScreen extends StatelessWidget {
  const AboutScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('About Us'),
      ),
      body: const Padding(
        padding: EdgeInsets.all(20),
        child: Center(
          child: Text(
            'This app was created by Grade 11 students '
            'to learn Flutter development.',
            textAlign: TextAlign.center,
            style: TextStyle(fontSize: 20),
          ),
        ),
      ),
    );
  }
}
```

Each page is an independent widget with its own `Scaffold` and `AppBar`.

## 11. Navigate Between Pages

### Open Students from Home

Update `home_screen.dart` with the following code:

``` dart
import 'package:flutter/material.dart';
import 'student_screen.dart';
import 'about_screen.dart';

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('School App'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Text(
              'Welcome to the School App!',
              style: TextStyle(fontSize: 22),
            ),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: () {
                Navigator.push(
                  context,
                  MaterialPageRoute(
                    builder: (context) =>
                        const StudentScreen(),
                  ),
                );
              },
              child: const Text('View Students'),
            ),
            const SizedBox(height: 12),
            ElevatedButton(
              onPressed: () {
                Navigator.push(
                  context,
                  MaterialPageRoute(
                    builder: (context) =>
                        const AboutScreen(),
                  ),
                );
              },
              child: const Text('About Us'),
            ),
          ],
        ),
      ),
    );
  }
}
```

Run the app and press each button.

### How does navigation work?

``` text
HomeScreen
   |
   | User presses "View Students"
   v
Navigator.push()
   |
   v
StudentScreen
   |
   | User presses Back
   v
HomeScreen
```

### Understand the navigation code

  Code                  Meaning
  --------------------- ------------------------------------------------------
  `Navigator`           Manages navigation between pages.
  `Navigator.push()`    Opens a new page on top of the current page.
  `context`             Identifies the widget's location in the widget tree.
  `MaterialPageRoute`   Defines a route and its transition.
  `builder`             Creates the destination page.
  `StudentScreen()`     Creates the destination screen widget.

Think of the navigation stack as a pile of books: a new page is placed
on top, and going back removes the top page to reveal the previous one.

### Return to the previous page

``` dart
Navigator.pop(context);
```

The Android back button normally returns to the previous route. You can
also use `Navigator.pop(context)` inside a custom Back button.

## 12. Pass Data Between Pages

A page often needs information from another page. For example, the
student list may open a details page and pass the student's name.

### Create `lib/screens/student_details_screen.dart`

``` dart
import 'package:flutter/material.dart';

class StudentDetailsScreen extends StatelessWidget {
  final String studentName;

  const StudentDetailsScreen({
    super.key,
    required this.studentName,
  });

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Student Details'),
      ),
      body: Center(
        child: Text(
          'Student Name: $studentName',
          style: const TextStyle(fontSize: 22),
        ),
      ),
    );
  }
}
```

### Understand the constructor

-   `final String studentName;` declares a string value that cannot be
    reassigned.
-   `required this.studentName` means the caller must provide the named
    argument.
-   `$studentName` inserts the value into the displayed string.

### Open the details page

In `student_screen.dart`, add this import:

``` dart
import 'student_details_screen.dart';
```

Replace the page's existing `body` with:

``` dart
body: Center(
  child: ElevatedButton(
    onPressed: () {
      Navigator.push(
        context,
        MaterialPageRoute(
          builder: (context) =>
              const StudentDetailsScreen(
            studentName: 'Kamal',
          ),
        ),
      );
    },
    child: const Text('View Kamal Details'),
  ),
),
```

The navigation flow is now:

``` text
HomeScreen
   └── StudentScreen
         └── StudentDetailsScreen
              Student Name: Kamal
```

**Extension activity:** Replace the fixed name with a name selected from
a list of students.

## 13. Create Reusable Widgets

If the same UI is needed on several pages, create it once and reuse it.

### Create `lib/widgets/welcome_card.dart`

``` dart
import 'package:flutter/material.dart';

class WelcomeCard extends StatelessWidget {
  final String title;
  final String message;

  const WelcomeCard({
    super.key,
    required this.title,
    required this.message,
  });

  @override
  Widget build(BuildContext context) {
    return Card(
      child: Padding(
        padding: const EdgeInsets.all(20),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text(
              title,
              style: const TextStyle(
                fontSize: 20,
                fontWeight: FontWeight.bold,
              ),
            ),
            const SizedBox(height: 8),
            Text(message),
          ],
        ),
      ),
    );
  }
}
```

### Use the reusable widget

In `home_screen.dart`, add:

``` dart
import '../widgets/welcome_card.dart';
```

The `..` moves up from `screens/` to `lib/`, then into `widgets/`.

Inside the `Column`'s `children` list, add:

``` dart
const WelcomeCard(
  title: 'Welcome Students',
  message: 'Learn Flutter step by step!',
),
```

You can reuse the same widget with different data:

``` dart
const WelcomeCard(
  title: 'Our School',
  message: 'Explore our school application.',
),
```

The class defines the UI once; each instance can display different
values.

## 14. Build a Counter Screen

Create `lib/screens/counter_screen.dart`:

``` dart
import 'package:flutter/material.dart';

class CounterScreen extends StatefulWidget {
  const CounterScreen({super.key});

  @override
  State<CounterScreen> createState() =>
      _CounterScreenState();
}

class _CounterScreenState extends State<CounterScreen> {
  int count = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Counter'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              'Count: $count',
              style: const TextStyle(fontSize: 28),
            ),
            ElevatedButton(
              onPressed: () {
                setState(() {
                  count++;
                });
              },
              child: const Text('Increase'),
            ),
            ElevatedButton(
              onPressed: () {
                setState(() {
                  count = 0;
                });
              },
              child: const Text('Reset'),
            ),
          ],
        ),
      ),
    );
  }
}
```

To open the counter from Home, import it in `home_screen.dart`:

``` dart
import 'counter_screen.dart';
```

Add another button inside the `Column`'s `children` list:

``` dart
ElevatedButton(
  onPressed: () {
    Navigator.push(
      context,
      MaterialPageRoute(
        builder: (context) => const CounterScreen(),
      ),
    );
  },
  child: const Text('Open Counter'),
),
```

### Key concepts

-   `StatefulWidget` is used because the displayed count changes.
-   `int count = 0` stores the count.
-   `onPressed` defines what happens when a button is pressed.
-   `setState()` notifies Flutter that the state has changed and the UI
    needs to be rebuilt.
-   `count++` increases the count by one.

**Challenge:** Change `count++` to `count = count + 2`. Predict the
result before running the app.

## 15. Build a Student Registration Form

Create `lib/screens/registration_screen.dart`:

``` dart
import 'package:flutter/material.dart';

class RegistrationScreen extends StatefulWidget {
  const RegistrationScreen({super.key});

  @override
  State<RegistrationScreen> createState() =>
      _RegistrationScreenState();
}

class _RegistrationScreenState
    extends State<RegistrationScreen> {
  final TextEditingController nameController =
      TextEditingController();

  String message = '';

  @override
  void dispose() {
    nameController.dispose();
    super.dispose();
  }

  void registerStudent() {
    final name = nameController.text.trim();

    setState(() {
      if (name.isEmpty) {
        message = 'Please enter your name.';
      } else {
        message = 'Welcome, $name!';
      }
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Student Registration'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(20),
        child: Column(
          children: [
            TextField(
              controller: nameController,
              decoration: const InputDecoration(
                labelText: 'Student Name',
                border: OutlineInputBorder(),
              ),
            ),
            const SizedBox(height: 16),
            ElevatedButton(
              onPressed: registerStudent,
              child: const Text('Register'),
            ),
            const SizedBox(height: 16),
            Text(message),
          ],
        ),
      ),
    );
  }
}
```

### Explain the important parts

-   `TextEditingController` reads the text entered by the user.
-   `nameController.text` retrieves the entered text.
-   `.trim()` removes whitespace from the beginning and end.
-   `if (name.isEmpty)` checks whether the field is empty.
-   `setState()` updates the message displayed on screen.
-   `dispose()` releases the controller when the widget is removed.

This is a demonstration form only. It does not save information to a
database.

**Extension activity:** Add an email field and display a message if
either field is empty.

## 16. Named Routes

Direct navigation using `MaterialPageRoute` is suitable for small
beginner projects. Named routes are another way to organise navigation
when an app has several pages.

For more complex applications, Flutter's `Router` APIs or packages such
as `go_router` may be more suitable. Named routes are still useful for
learning the basic idea of route names.

### Update `main.dart`

``` dart
import 'package:flutter/material.dart';
import 'screens/home_screen.dart';
import 'screens/student_screen.dart';
import 'screens/about_screen.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'School App',
      initialRoute: '/',
      routes: {
        '/': (context) => const HomeScreen(),
        '/students': (context) => const StudentScreen(),
        '/about': (context) => const AboutScreen(),
      },
    );
  }
}
```

### Navigate by route name

For the Students button:

``` dart
Navigator.pushNamed(context, '/students');
```

For the About button:

``` dart
Navigator.pushNamed(context, '/about');
```

To return:

``` dart
Navigator.pop(context);
```

The route table maps a route name to the screen Flutter should create.

  Route         Destination
  ------------- -----------------
  `/`           `HomeScreen`
  `/students`   `StudentScreen`
  `/about`      `AboutScreen`

For this exercise, use either direct `MaterialPageRoute` navigation or
named routes consistently. Avoid mixing both methods until students
understand each one.

## 17. Imports and Common Errors

Beginners commonly encounter errors due to incorrect file paths, missing
imports, spelling mistakes or mismatched brackets.

### Import examples

If the file is `lib/screens/home_screen.dart`, this import is valid in
`main.dart`:

``` dart
import 'screens/home_screen.dart';
```

If the file is `lib/widgets/welcome_card.dart`, this import is valid in
`home_screen.dart`:

``` dart
import '../widgets/welcome_card.dart';
```

You can also use a package import:

``` dart
import 'package:my_first_app/screens/home_screen.dart';
```

Here, `my_first_app` must match the package name in `pubspec.yaml`.

### Naming conventions

-   Dart file names: lowercase with underscores, for example
    `home_screen.dart`.
-   Widget class names: UpperCamelCase, for example `HomeScreen`.
-   Variable names: lowerCamelCase, for example `studentName`.
-   Constants: follow Dart's standard naming conventions and use `const`
    when a value is compile-time constant.

### Troubleshooting table

  ---------------------------------------------------------------------------
  Problem                                 What to check
  --------------------------------------- -----------------------------------
  `Target of URI doesn't exist`           Check the file path and spelling in
                                          the import.

  `Undefined class 'HomeScreen'`          Check the import and class name.

  `Expected to find ')'`                  Check parentheses, braces and
                                          commas.

  `No named parameter with the name...`   Check the widget constructor's
                                          parameters.

  Screen is blank or unexpected           Check the widget tree, `home`,
                                          `body` and runtime errors.

  Button does nothing                     Check the `onPressed` callback.

  Counter does not update                 Check that the state change is
                                          inside `setState()`.
  ---------------------------------------------------------------------------

### A useful debugging routine

1.  Read the first error shown in the console.
2.  Check the file and line number mentioned.
3.  Check spelling, brackets, commas and imports.
4.  Fix one problem at a time.
5.  Save and run the app again.

## 18. Final Project Structure

After completing the guide, your project may look like this:

``` text
lib/
├── main.dart
├── screens/
│   ├── home_screen.dart
│   ├── student_screen.dart
│   ├── student_details_screen.dart
│   ├── about_screen.dart
│   ├── counter_screen.dart
│   └── registration_screen.dart
└── widgets/
    └── welcome_card.dart
```

A `models/` folder can be added when students start creating structured
data classes, such as a `Student` model.

Do not create a new folder for every class. Group files when they share
a clear purpose.

## 19. Grade 11 Mini Project

# School App

Build a simple school application that demonstrates what you have
learned.

### Required features

1.  **Home page:** School title and welcome message.
2.  **Students page:** At least three sample student names.
3.  **Student details page:** Receives and displays a selected student's
    name.
4.  **About page:** A short description of the app or school.
5.  **Navigation:** Buttons to open pages and a working back action.
6.  **Registration form:** Reads a name and checks that it is not empty.
7.  **Code organisation:** Screens are stored in separate files and
    reusable UI is placed in `widgets/`.

### Suggested development order

1.  Create and run `main.dart`.
2.  Build the Home screen.
3.  Create `student_screen.dart` and `about_screen.dart`.
4.  Add navigation.
5.  Pass a name to the student details page.
6.  Add the counter and registration form.
7.  Review the file structure and fix errors.
8.  Demonstrate the app and explain how it works.

For this first project, students do not need a database, Firebase,
authentication or internet access. Use sample data and focus on Flutter
fundamentals.

## 20. Suggested Teaching Plan

Split the material into four practical lessons rather than rushing
through every concept in one sitting.

### Lesson 1 --- Start from zero

**Topics:** Imports, `main()`, `runApp()`, `MaterialApp`, `Scaffold`,
`Text`, `Column`, `Row`, `AppBar` and buttons.

**Practical outcome:** A working single-page welcome app.

### Lesson 2 --- Files and folders

**Topics:** Create `screens/`, create a Dart file, define a widget class
and import it into `main.dart`.

**Practical outcome:** A clean project with separate screens.

### Lesson 3 --- Navigation

**Topics:** `Navigator.push()`, `Navigator.pop()`, passing values
through constructors and named routes.

**Practical outcome:** A working multi-page app.

### Lesson 4 --- Interaction and mini project

**Topics:** `StatefulWidget`, counters, `TextField`, basic validation
and reusable widgets.

**Practical outcome:** A small school app interface.

## 21. Student Practice Activities

Complete these tasks after following the examples:

-   [ ] **Activity 1 --- Change the welcome screen:** Change the title,
    message, text size and colours.
-   [ ] **Activity 2 --- Create an About page:** Create
    `about_screen.dart` and navigate to it using a button.
-   [ ] **Activity 3 --- Pass student data:** Pass a student's name from
    `StudentScreen` to `StudentDetailsScreen`.
-   [ ] **Activity 4 --- Build a counter:** Create Increase and Reset
    buttons and display the count.
-   [ ] **Activity 5 --- Create a registration form:** Read a name from
    a `TextField` and show a validation message.
-   [ ] **Activity 6 --- Explain the project:** Explain the role of
    `main.dart`, one screen file, one import and one navigation action.

## 22. Assessment Rubric

  Criterion                                            Marks
  ------------------------------------------------ ---------
  Correct use of `main.dart` and Flutter widgets          20
  Separate files, folders and imports                     20
  Navigation between pages                                20
  UI design and layout                                    15
  State management and form interaction                   15
  Code readability and demonstration                      10
  **Total**                                          **100**

## 23. Final Tips

Follow this learning sequence:

**One working screen → understand the widget tree → move the screen into
a separate file → create a second page → navigate → pass data → add
interaction → organise and improve the app.**

For beginners, understanding the entry point, widget classes, imports
and navigation is more important than learning advanced architecture,
APIs or Firebase immediately.

### Quick reference

  Need to...                     Use...
  ------------------------------ -------------------------
  Start the app                  `main()` and `runApp()`
  Set up a Material app          `MaterialApp`
  Create a standard page         `Scaffold`
  Display text                   `Text`
  Arrange widgets vertically     `Column`
  Arrange widgets horizontally   `Row`
  Add spacing                    `SizedBox` or `Padding`
  Open a page                    `Navigator.push()`
  Return to the previous page    `Navigator.pop()`
  Open a named route             `Navigator.pushNamed()`
  Update simple UI state         `setState()`
  Read text input                `TextEditingController`
  Reuse a UI component           Create a custom widget

------------------------------------------------------------------------

**Happy coding!** Build one feature at a time, run your app frequently,
read the errors carefully, and make sure you understand the code you
write.
