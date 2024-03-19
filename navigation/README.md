## main.dart
```dart
import 'package:flutter/material.dart';

import 'pages/home_page.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: MyHomePage(),
    );
  }
}

```

## home_page.dart

```dart
import 'package:flutter/material.dart';
import 'package:lecture_07/pages/other_page.dart';

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.amber,
        title: Text(
          'App Name',
          style: TextStyle(
            fontWeight: FontWeight.bold,
          ),
        ),
        foregroundColor: Colors.white,
        centerTitle: true,
        leading: Icon(
          Icons.accessibility,
          size: 48,
          color: Colors.teal,
        ),
        actions: [
          IconButton(
            onPressed: () {},
            icon: Icon(Icons.settings),
          )
        ],
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              'Home Page',
              style: TextStyle(fontSize: 40),
            ),
            TextButton(
              onPressed: () {
                Navigator.push(
                  context,
                  MaterialPageRoute(
                    builder: (context) {
                      return OtherPage();
                    },
                  ),
                );
              },
              child: Text(
                'Go to Other Page',
                style: TextStyle(fontSize: 30),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

```

## other_page.dart

```dart
import 'package:flutter/material.dart';

class OtherPage extends StatelessWidget {
  const OtherPage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(),
      body: Center(
        child: Column(
          children: [
            Text('Other Page'),
            TextButton(
              onPressed: () {
                Navigator.pop(context);
              },
              child: Text('Go Back'),
            ),
          ],
        ),
      ),
    );
  }
}

```


## container.dart
```dart

import 'package:flutter/material.dart';

class ContainerWidget extends StatelessWidget {
  const ContainerWidget({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Container(
              width: 250,
              height: 150,
              decoration: BoxDecoration(
                color: Colors.amber,
                borderRadius: BorderRadius.circular(24),
                gradient: LinearGradient(
                  colors: [
                    Colors.red,
                    Colors.pink,
                  ],
                ),
              ),
              child: Center(
                child: Text(
                  'Hello World',
                  style: TextStyle(
                    fontSize: 30,
                    color: Colors.white,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

```