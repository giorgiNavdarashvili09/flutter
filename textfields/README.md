
## main.dart
```dart

import 'package:flutter/material.dart';
import 'package:lecture_04/text_box_screen.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: TextBoxScreen(),
      ),
    );
  }
}
```


## TextBoxScreen

```dart
import 'package:flutter/material.dart';

class TextBoxScreen extends StatefulWidget {
  @override
  State<TextBoxScreen> createState() {
    return _TextBoxScreenState();
  }
}

class _TextBoxScreenState extends State<TextBoxScreen> {
  bool isObscure = true;

  bool isVisible = false;

  TextEditingController emailController = TextEditingController();
  TextEditingController passwordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Container(
      margin: EdgeInsets.symmetric(horizontal: 32),
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          CircleAvatar(
            radius: 64,
            child: Container(
              width: 64,
              child: Image.network(
                  'https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/User_icon-cp.png/1200px-User_icon-cp.png'),
            ),
          ),
          SizedBox(
            height: 32,
          ),
          TextField(
            controller: emailController,
            decoration: InputDecoration(
              border: OutlineInputBorder(),
              label: Text(
                'Email',
                style: TextStyle(
                  fontSize: 22,
                ),
              ),
              prefixIcon: Icon(
                Icons.email,
              ),
              suffixIcon: IconButton(
                onPressed: () {
                  emailController.clear();
                },
                icon: Icon(Icons.clear),
              ),
            ),
          ),
          SizedBox(
            height: 16,
          ),
          TextField(
            controller: passwordController,
            obscureText: isObscure,
            decoration: InputDecoration(
              border: OutlineInputBorder(),
              label: Text(
                'password',
                style: TextStyle(fontSize: 22),
              ),
              prefixIcon: Icon(Icons.key),
              suffixIcon: IconButton(
                onPressed: () {
                  setState(() {
                    isObscure = !isObscure;
                  });
                },
                icon: Icon(Icons.visibility),
              ),
            ),
          ),
          SizedBox(
            height: 32,
          ),
          Visibility(visible: isVisible, child: Text('Hello Flutter')),
          SizedBox(
            height: 32,
          ),
          ElevatedButton(
              onPressed: () {
                setState(() {
                  isVisible = !isVisible;
                });
              },
              child: Container(
                padding: EdgeInsets.symmetric(horizontal: 32, vertical: 8),
                child: Text(
                  'Sign In',
                  style: TextStyle(fontSize: 22),
                ),
              )),
        ],
      ),
    );
  }
}

```