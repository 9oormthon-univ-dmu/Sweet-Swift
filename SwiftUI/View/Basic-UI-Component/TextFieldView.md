# TextField View

SwiftUI에서 사용자가 텍스트를 입력할 수 있는 입력 상자를 TextField라고 한다.

## 기본 구조

SwiftUI에서 텍스트 필드 뷰는 `TextField` 구조체를 사용하여 생성한다.
텍스트 필드는 입력된 텍스트를 저장할 변수를 바인딩하여 사용한다.

<br>

```swift
@State private var name: String = ""

var body: some View {
  TextField("이름을 입력해주세요.", text: $name)
}
```
<br>

여기서 TextField에 "텍스트" 부분은 placeholder로 어떤 값을 입력해야 하는지 알려준다.

## 스타일

텍스트 필드에는 다양한 모디파이어를 사용하여 커스텀할 수 있는데 기존에 Text에서 언급하지 않은 모디파이어 위주로 내용을 작성하려고 한다.

#### 배경색과 테두리

텍스트 필드의 배경섹을 바꾸기 위해서는 `.background()` 모디파이어를 사용한다.

<br>

```swift
TextField("이름을 입력해주세요.", text: $name)
  .background(Color.gray)
```

<br>

텍스트 필드의 테두리를 적용하기 위해서는 `.border()` 모디파이어를 사용한다.
border 모디파이어 안에는 색상, 굵기를 지정할 수 있다.

<br>

```swift
TextField("이름을 입력해주세요.", text: $name)
  .border(Color.black, width: 1)
```

<br>

텍스트 필드의 모서리를 둥글게 하기 위해서는 `.cornerRadius()` 모디파이어를 사용한다.

<br>

```swift
TextField("이름을 입력해주세요.", text: $name)
  .cornerRadius(5)
```

<br>

## 상호작용

텍스트 필드의 다양한 상호작용을 처리해보자!

#### 입력 이벤트 처리

`onEditingChanged` 와 `onCommit` 모디파이어를 사용해서 텍스트 필드의 입력 이벤트를 처리할 수 있다.

- `onEditingChanged` : 사용자가 텍스트 필드를 편집하기 시작하거나 끝낼 때 호출됨
- `onCommit` : 사용자가 텍스트 필드의 입력을 완료하고 엔터 키를 눌렀을 때 호출됨

<br>

```swift
TextField("이름을 입력해주세요.", text: $name, onEditingChanged: {
isEditing in
  print("작성중")
}, onCommit: {
  print("입력완료")
})
```

<br>

## 키보드 타입 설정

텍스트 필드는 키보드 타입을 설정하여 사용자가 특정 값을 입력할 수 있도록 할 수 있다.
`keyboardType` 모디파이어를 사용하여 키보드 타입을 설정한다.

```swift
TextField("이메일을 입력해주세요.", text: $email)
  .keyboardType(.emailAddress)
```

## placeholder 스타일

placeholder 스타일을 설정할 수 있다. 텍스트 필드가 비어 있을 때 표시되는 텍스트의 스타일을 지정할 수 있다.

```swift
TextField("", text: $name)
  .placeholder(when: name.isEmpty) {
    Text("이름을 입력하세요.")
  }
```

# SecureField View

비밀번호 입력 필드와 같은 보안 텍스트 입력을 위해서는 `SecureField`를 사용할 수 있다.
입력된 텍스트를 보이지 않게 처리한다.

```swift
@State private var password: String = ""

var body: some View {
  SecureField("비밀번호를 입력해주세요.", text: $password)
}
```
