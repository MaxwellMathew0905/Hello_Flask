```dart
// =========================================
// FLUTTER MAP PRACTICAL - COMPLETE SINGLE FILE
// Covers Q1 to Q8
// =========================================

import 'package:flutter/material.dart';
// Uncomment for Firebase (Q5)
// import 'package:firebase_core/firebase_core.dart';
// import 'package:cloud_firestore/cloud_firestore.dart';

void main() {
  runApp(MyApp());
}

// =========================================
// MAIN APP
// =========================================
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,

      // 🔥 CHANGE THIS LINE IN EXAM BASED ON QUESTION
      home: HomePage(), 
      // home: CalculatorPage(),
      // home: FormPage(),
      // home: CollegePage(),
    );
  }
}

// =========================================
// Q1, Q2, Q3 - DISPLAY PAGE
// =========================================
class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Display Page")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Image.asset("assets/image.jpg", height: 150),
            SizedBox(height: 20),
            Text("Welcome Page"),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.menu),
        onPressed: () {
          Navigator.push(
            context,
            MaterialPageRoute(builder: (context) => MenuPage()),
          );
        },
      ),
    );
  }
}

// =========================================
// Q1, Q2, Q3 - MENU PAGE
// Modify items for Food / Books / Mobiles
// =========================================
class MenuPage extends StatelessWidget {
  final List items = [
    {"name": "Item 1", "price": 100},
    {"name": "Item 2", "price": 200},
    {"name": "Item 3", "price": 300},
    {"name": "Item 4", "price": 400},
    {"name": "Item 5", "price": 500},
    {"name": "Item 6", "price": 600},
    {"name": "Item 7", "price": 700},
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Menu Page")),
      body: ListView.builder(
        itemCount: items.length,
        itemBuilder: (context, index) {
          return ListTile(
            leading: Icon(Icons.image),
            title: Text(items[index]['name']),
            subtitle: Text("₹${items[index]['price']}"),
          );
        },
      ),
    );
  }
}

// =========================================
// Q4 - CALCULATOR
// =========================================
class CalculatorPage extends StatefulWidget {
  @override
  _CalculatorPageState createState() => _CalculatorPageState();
}

class _CalculatorPageState extends State<CalculatorPage> {
  String output = "";

  void press(String value) {
    setState(() {
      if (value == "C") {
        output = "";
      } else {
        output += value;
      }
    });
  }

  @override
  Widget build(BuildContext context) {
    List<String> buttons = [
      "1","2","3","+",
      "4","5","6","-",
      "7","8","9","*",
      "0","/","C"
    ];

    return Scaffold(
      appBar: AppBar(title: Text("Calculator")),
      body: Column(
        children: [
          Container(
            padding: EdgeInsets.all(20),
            alignment: Alignment.centerRight,
            child: Text(output, style: TextStyle(fontSize: 30)),
          ),
          Expanded(
            child: GridView.count(
              crossAxisCount: 4,
              children: buttons.map((btn) {
                return ElevatedButton(
                  onPressed: () => press(btn),
                  child: Text(btn),
                );
              }).toList(),
            ),
          )
        ],
      ),
    );
  }
}

// =========================================
// Q5 & Q8 - REGISTRATION / LOGIN FORM
// =========================================
class FormPage extends StatelessWidget {
  final TextEditingController name = TextEditingController();
  final TextEditingController email = TextEditingController();

  void submit() {
    // Firebase integration (optional)
    /*
    FirebaseFirestore.instance.collection("users").add({
      "name": name.text,
      "email": email.text,
    });
    */
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Registration Form")),
      body: Padding(
        padding: EdgeInsets.all(20),
        child: Column(
          children: [
            TextField(
              controller: name,
              decoration: InputDecoration(labelText: "Name"),
            ),
            TextField(
              controller: email,
              decoration: InputDecoration(labelText: "Email"),
            ),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: submit,
              child: Text("Submit"),
            )
          ],
        ),
      ),
    );
  }
}

// =========================================
// Q6 - COLLEGE WEBSITE UI
// =========================================
class CollegePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("My College")),
      drawer: Drawer(
        child: ListView(
          children: [
            ListTile(title: Text("About Us")),
            ListTile(title: Text("Academics")),
            ListTile(title: Text("Library")),
            ListTile(title: Text("Placements")),
            ListTile(title: Text("Admissions")),
          ],
        ),
      ),
      body: Column(
        children: [
          SizedBox(height: 20),
          Text("Announcements", style: TextStyle(fontSize: 20)),
          Text("Admissions Open Now!"),
        ],
      ),
    );
  }
}

// =========================================
// Q7 - WEB MANIFEST (WRITE IN THEORY)
// =========================================
/*
{
  "name": "My App",
  "short_name": "App",
  "start_url": ".",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#000000",
  "icons": [
    {
      "src": "icon.png",
      "sizes": "192x192",
      "type": "image/png"
    }
  ]
}
*/

// =========================================
// Q8 - TEST CASES (WRITE IN PAPER)
// =========================================
/*
Test Case 1:
Input: Valid Email & Password
Output: Login Successful

Test Case 2:
Input: Empty Fields
Output: Error Message
*/
// =========================================
```





import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

// MAIN APP
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: DisplayPage(),
    );
  }
}

// DISPLAY PAGE
class DisplayPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Restaurant")),

      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Image.network("https://via.placeholder.com/150"),
            Text("My Restaurant"),
          ],
        ),
      ),

      floatingActionButton: FloatingActionButton(
        child: Icon(Icons.add),
        onPressed: () {
          Navigator.push(
            context,
            MaterialPageRoute(builder: (context) => MenuPage()),
          );
        },
      ),
    );
  }
}

// MENU PAGE
class MenuPage extends StatelessWidget {

  final List food = [
    {"name": "Pizza", "price": 200},
    {"name": "Burger", "price": 150},
    {"name": "Pasta", "price": 180},
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Menu")),

      body: ListView.builder(
        itemCount: food.length,
        itemBuilder: (context, index) {
          return ListTile(
            leading: Icon(Icons.fastfood),
            title: Text(food[index]['name']),
            subtitle: Text("₹${food[index]['price']}"),
          );
        },
      ),
    );
  }
}
