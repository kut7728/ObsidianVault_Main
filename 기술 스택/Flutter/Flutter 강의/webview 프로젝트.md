---
설명: "[웹뷰, 웹뷰 컨트롤러, .. 함수]"
상위 항목:
  - "[[인프런 강의]]"
하위 항목:
  - "[[함수사이 ‘ .. ‘ 의 쓰임새]]"
  - "[[WebView 위젯]]"
---
### flutter package 사이트

> [!important] pub.dev

  

```Dart
import 'package:flutter/material.dart';
import 'package:webview_flutter/webview_flutter.dart';

final homeurl = Uri.parse('https://blog.codefactory.ai');

class HomeScreen extends StatelessWidget {
  WebViewController controller = WebViewController()
    ..loadRequest(homeurl)
    ..setJavaScriptMode(JavaScriptMode.unrestricted);

  HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        // titleTextStyle: TextStyle(color: Colors.white),
        title: Text('Code Factory'),
        centerTitle: true,
        backgroundColor: Colors.orange[600],
        actions: [
          IconButton(
            onPressed: () {
              controller.loadRequest(homeurl);
            },
            icon: Icon(
              Icons.home,
            ),
          )
        ],
      ),
      body: WebViewWidget(controller: controller),
    );
  }
}
```