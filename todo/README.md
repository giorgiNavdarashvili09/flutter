### main.dar
```dart
import 'package:flutter/material.dart';
import 'todo_screen.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: TodoScreen(),
      ),
    );
  }
}

```

### TodoScreen ვიჯეტი
```dart
import 'package:flutter/material.dart';
import 'package:todo/todo.dart';

class TodoScreen extends StatefulWidget {
  const TodoScreen({Key? key}) : super(key: key);

  @override
  State<TodoScreen> createState() => _TodoScreenState();
}

class _TodoScreenState extends State<TodoScreen> {
  TodoList todos = TodoList();

  TextEditingController titleController = TextEditingController();
  TextEditingController descriptionController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Expanded(
          child: ListView.builder(
            itemCount: todos.todoItems.length,
            itemBuilder: (context, index) {
              return ListTile(
                title: Text(todos.todoItems[index].title),
                subtitle: Text(todos.todoItems[index].description),
              );
            },
          ),
        ),
        Row(
          children: [
            SizedBox(
              width: 24,
            ),
            Expanded(
              child: Column(
                children: [
                  SizedBox(
                    height: 24,
                  ),
                  TextField(
                    controller: titleController,
                    decoration: InputDecoration(
                      label: Text('Title'),
                      border: OutlineInputBorder(),
                    ),
                  ),
                  SizedBox(
                    height: 24,
                  ),
                  TextField(
                    controller: descriptionController,
                    decoration: InputDecoration(
                      label: Text('Description'),
                      border: OutlineInputBorder(),
                    ),
                  ),
                  SizedBox(
                    height: 24,
                  ),
                ],
              ),
            ),
            SizedBox(
              width: 24,
            ),
            ElevatedButton(
              onPressed: () {
                setState(() {
                  todos.addTodo(
                    TodoItem(
                      title: titleController.text,
                      description: descriptionController.text,
                    ),
                  );
                });
              },
              child: Text('Add'),
            ),
            SizedBox(
              width: 24,
            ),
          ],
        ),
      ],
    );
  }
}

```


## todo.dart

```dart
class TodoItem {
  String title;
  String description;

  TodoItem({required this.title, required this.description});

  String toString() {
    return 'TodoItem{title: $title, description: $description}';
  }
}

class TodoList {
  List<TodoItem> todoItems = [];

  void addTodo(TodoItem todoItem) {
    todoItems.add(todoItem);
  }

  void removeTodo(TodoItem todoItem) {
    todoItems.remove(todoItem);
  }

  void printTodoList() {
    for (int i = 0; i < todoItems.length; i++) {
      print('${todoItems[i]}');
    }
  }
}


```