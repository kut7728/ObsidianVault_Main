---
설명: 버튼은 상호작용이 있어서 스타일링 방법이 다르다!
상위 항목:
  - "[[랜덤숫자 생성기 프로젝트]]"
---
```Dart
class _Footer extends StatelessWidget {
  final VoidCallback onPressed;

  const _Footer({super.key, required this.onPressed});

  @override
  Widget build(BuildContext context) {
    return ElevatedButton(
      onPressed: onPressed,
      style: ElevatedButton.styleFrom(
        backgroundColor: redColor,
        foregroundColor: Colors.white,
      ),
      child: Text(
        '생성하기!',
      ),
    );
  }
}
```