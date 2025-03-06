---
설명: Build함수에서 비동기 함수 사용하는 방법
상위 항목:
  - "[[‘오늘도 출근’ 프로젝트]]"
---
```Dart
@override
  Widget build(BuildContext context) {
    return Scaffold(
      body: FutureBuilder(
	      // 사용할 비동기 함수 집어넣기
        future: checkPermission(),
        // snapshot - 함수의 결과물 받는 곳, 반환된 ui 보여줌
        builder: (BuildContext context, AsyncSnapshot snapshot) {
          if (snapshot.hasError) {
            return Center(
              child: Text(snapshot.error.toString()),
            );
          }
          return Column(
            children: [
              Expanded(
                child: GoogleMap(
                  initialCameraPosition: initialPosition,
                ),
              )
            ],
          );
        },
      ),
    );
  }
```