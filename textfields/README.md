```dart
import 'package:flutter/material.dart';

class TextBoxScreen extends StatefulWidget {
  @override
  State<TextBoxScreen> createState() {
    return _TextBoxScreenState();
  }
}

class _TextBoxScreenState extends State<TextBoxScreen> {
  @override
  Widget build(BuildContext context) {
    return Container(
      margin: EdgeInsets.symmetric(horizontal: 32),
      child: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          TextField(
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
            ),
          ),
          SizedBox(
            height: 16,
          ),
          TextField(
            obscureText: true,
            decoration: InputDecoration(
              border: OutlineInputBorder(),
              label: Text(
                'password',
                style: TextStyle(fontSize: 22),
              ),
              prefixIcon: Icon(Icons.key),
            ),
          ),
          SizedBox(
            height: 32,
          ),
          TextButton(
              onPressed: () {},
              child: Text(
                'Sign In',
                style: TextStyle(fontSize: 22),
              )),
        ],
      ),
    );
  }
}


 ```