---
상위 항목:
  - "[[코딩애플 강의]]"
---
![[Assets/Untitled 16.png|Untitled 16.png]]

  

- 코드
    
    ```Dart
    import 'package:flutter/material.dart';
    
    void main() {
      runApp(const MyApp());
    }
    
    class MyApp extends StatelessWidget {
      const MyApp({super.key});
    
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
            home: Scaffold(
          appBar: AppBar(
            titleTextStyle: TextStyle(fontSize: 20, color: Colors.white),
            centerTitle: false,
            backgroundColor: Colors.blue,
            title: Text('앱임'),
          ),
          body: Text('안녕'),
          bottomNavigationBar: BottomAppBar(
            child: Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                Icon(Icons.phone),
                Icon(Icons.message),
                Icon(Icons.contact_page),
              ],
            ),
          ),
        ));
      }
    }
    ```