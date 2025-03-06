#UIKit 

# 개요
앱이 실행되는 동안 기본저장소에 접근하여 데이터를 기록, 조회하는 역할

- key-value 쌍으로 저장
- 싱글톤 패턴으로 앱 전역적으로 하나의 객체만 존재

# 구현
## 저장
```swift
func saveTasks() {
        
        //userDefault에는 키-밸류 형식으로 저장
        let data = self.tasks.map {
            [
                "title": $0.title,
                "done": $0.done
            ]
        }
        let userDefaults = UserDefaults.standard  // 싱글톤 패턴의 객체를 참조
        userDefaults.set(data, forKey: "tasks") // set메서드로 (저장데이터, 키값)의 형태로 저장
    }
```

## 조회
```swift 
func loadTasks() {
        let userDefaults = UserDefaults.standard // userDefault 접근
        
        guard let data = userDefaults.object(forKey: "tasks") as? [[String: Any]] else { return } //키를 통해 밸류 참조
        self.tasks = data.compactMap {  // tasks 배열에 데이터 장착, compactMap으로 nil 제외
            guard let title = $0["title"] as? String else { return nil }
            guard let done = $0["done"] as? Bool else { return nil }
            return Task(title: title, done: done)
        }
    }
```