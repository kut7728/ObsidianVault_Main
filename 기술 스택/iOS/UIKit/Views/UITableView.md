#UIKit #UIKit-View 

# 개요
- 데이터를 리스트 형태로 보여줄 수 있는 가장 기본적인 UI 컴포넌트
- 스크롤 뷰 상속함
- 리스트 형태로만 보여줄 수 있음 ([[UICollectionView]]와의 차이점)

# 특징
- UIScrollView를 상속받고 있어 스크롤 가능
- 섹션으로 행을 그룹화 가능
- 섹션의 헤더/푸터에 뷰를 구성하여 추가적인 정보 표시 가능

# 구현 방법
- UITableViewDataSource 프로토콜 채택 - 데이터를 받아 뷰를 그려주는 역할
	- numberOfRowsInSection 메서드 필수 구현 → ==각 섹션에 표시할 행의 갯수==
	- cellForRowAt 메서드 필수 구현 → ==행을 그리기 위한 재사용 가능한 셀 설정==
- UITableViewDelegate 프로토콜 채택 - 테이블뷰의 동작과 외관을 담당

# 기능 구현
## ✅ UITableViewDataSource
### numberOfRowsInSection

```swift title:"각 섹션에 표시할 행의 갯수"
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return self.tasks.count
    }
```

### cellForRowAt

```swift title:"특정 행을 그리기 위한 셀을 반환"
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        
        //dequeReusableCell 메서드 : 제공한 withIdentifier 식별자로 재사용 가능한 cell 뷰를 tableView의 indexPath 위치에서 사용하도록 반환해줌
        let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: indexPath) // 스토리 보드에 구현한 셀 가져오기
        let task = self.tasks[indexPath.row]
        cell.textLabel?.text = task.title
        if task.done {
            cell.accessoryType = .checkmark
        } else {
            cell.accessoryType = .none
        }
        return cell
    }
```

### commit, forRowAt

```swift title:"편집모드에서 삭제버튼 눌렀을때 눌린 셀이 어떤놈인지 알려주는 메서드 & 스와이프해서 삭제 기능 구현해줌"
    func tableView(_ tableView: UITableView, commit editingStyle: UITableViewCell.EditingStyle, forRowAt indexPath: IndexPath) {
        self.tasks.remove(at: indexPath.row)  // 눌린 셀의 데이터 삭제
        tableView.deleteRows(at: [indexPath], with: .automatic) // 삭제된 셀의 인덱스를 받아서 셀 삭제
        
        // 모든 할일을 삭제했을때 자동으로 편집모드에서 탈출
        if self.tasks.isEmpty {
            self.doneButtonTap()
        }
    }
```

### canMoveRowAt
```swift title:"셀이 이동가능한지 알려주는 메서드... 그냥 true 반환하도록 짜면 됨;;"
    func tableView(_ tableView: UITableView, canMoveRowAt indexPath: IndexPath) -> Bool {
        return true
    }
```

### MoveRowAt
```swift title:"순서가 이동할 셀의 인덱스와 이동할 위치의 인덱스 알려주는 메서드"
    func tableView(_ tableView: UITableView, moveRowAt sourceIndexPath: IndexPath, to destinationIndexPath: IndexPath) {
        
        // 데이터의 배열 수정
        var tasks = self.tasks
        let task = tasks[sourceIndexPath.row]
        tasks.remove(at: sourceIndexPath.row)
        tasks.insert(task, at: destinationIndexPath.row)
        self.tasks = tasks
    }
```

## ✅ UITableViewDelegate
### didSelectRowAt
```swift title:"셀을 선택했을때 어떤 셀이 선택됐는지 알려주는 메서드"
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        var task = self.tasks[indexPath.row]
        task.done.toggle()
        self.tasks[indexPath.row] = task
        // 선택된 셀 갱신, 배열로 전체 리스트 갱신도 가능하지만 여기서는 선택된 셀만
        self.tableView.reloadRows(at: [indexPath], with: .automatic) // with: - 셀의 변동에 따른 애니메이션 설정
    }
```

## ✅ 메서드
### `.selfEditing()` - 편집모드 토글

```swift
self.tableView.setEditing(false, animated: true)
```

