# Button

버튼은 사용자가 뷰와 직접 상호작용할 수 있는 요소로, 특정 작업을 수행하는 데 사용된다.

## 기본 구조

<br>

```swift
Button(action: {
  // Action: 동작할 내용
}) {
  // Label: 버튼 내부 텍스트
  Text("확인")
}
```

<br>

버튼은 두 가지 주요 요소로 구성된다.

1. Action: 버튼이 눌렸을 때 실행되는 클로저
2. Label: 버튼의 외형을 정의하는 뷰

#### 액션

액션은 버튼이 눌렸을 때 실행되는 코드이다. 
일반적으로 상태를 변경하거나, 특정 작업을 수행하는 데 사용된다.

#### 레이블

레이블은 텍스트, 이미지 또는 여러 조합으로 구성할 수 있으며, 버튼을 커스텀할 수 있다.

<br>

```swift
Button(action: {
  print("클릭")
}) {
  Text("완료")
    .font(.title)
    .background(Color.black)
    .foregroundColor(Color.white)
    .cornerRadius(10)
}
```

<br>

## 상태 관리

SwiftUI의 상태 관리는 `@State` 속성을 사용한다.
뷰의 상태를 저장하고 관리하며, 상태가 변경되면 해당 뷰를 다시 렌더링한다.

<br>

```swift
@State private var count = 0

Button(action: {
  self.count += 1
}) {
  Text("\(count)번 눌렸어요!")
}
```

<br>

이 코드로는 버튼이 눌릴 때마다 값이 증가하게 되고, 값이 변경될 때마다 뷰가 다시 그려지는 즉, 렌더링한다.

## 상호작용

버튼의 주요 기능은 사용자의 상호작용을 처리하는 것이다.
다음은 버튼의 다양한 상호작용을 처리하는 방법이다.

#### 활성화 상태 제어

버튼의 활성화 상태를 제어할 수 있다. 
예를 들어서 회원가입을 할 때 모든 값이 입력되지 않으면 disabled를 true, 모든 값이 입력되었을 때만 disabled를 false로 변경되게 활성화 상태를 제어하게 된다.

<br>

```swift
@State private var isDisabled = true

Button(action: {
  print("클릭")
}) {
  Text("완료")
}
.disabled(isDisabled)
```

<br>

#### 긴 누르기 액션

`.onLongPressGesture` 모디파이어를 사용하면 버튼이 길게 눌렸을 때의 액션을 정의할 수 있따.

<br>

```swift
Button(action: {
  print("클릭")
}) {
  Text("완료")
}
.onLongPressGesture {
  print("버튼이 길게 눌렸어요!")
}
```

<br>
