---
설명: 위젯 트리에서의 위젯의 위치 정보를 소유
상위 항목:
  - "[[인프런 강의]]"
---
> [!important] 모든 위젯은 실행시 createElement() 함수를 실행하면서
> 
> 위젯에 대한 정보(부모-자식이 누구인지, 크기가 얼마인지, 어떤 위젯인지 등등)를 가진
> 
> Element를 생성함
> 
>   
> 
> 이때 Element는 BuildContext를 implement(따라서 작성) 해야함 → 즉 Element = BuildContext

  

- stateless 위젯의 context는 전역적으로 접근이 불가능
- stateful 위젯의 context는 접근 가능