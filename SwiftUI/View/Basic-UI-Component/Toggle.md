# Toggle

토글은 스위치처럼 꺼짐과 켜짐 상태를 전환하는 컨트롤러이다.

<img width="91" alt="image" src="https://github.com/user-attachments/assets/59df8090-d804-4502-b7c8-05c476a5a181">

## 기본 구조

<br>

```swift
@State private var isOnAlert = false

var body: some View {
  Toggle("알림 설정", isOn: $isOnAlert)
    .toogleStyle(SwitchToggleStyle(tint: Color.yellow))
}
```

<br>

토글은 Boolean 타입으로 정의한 변수를 사용한다.
또한 토글의 색상을 변경하고 싶을 경우 `.toggleStyle()` 모디파이어를 통해 변경할 수 있다.
