# Stack

Stack은 여러 뷰를 수직 또는 수평으로 정렬하기 위해 사용되는 레이아웃 컨테이너이다.
스택은 뷰를 정렬하거나 배치하는 데 있어 매우 중요한 역할을 하고, UI를 구성하는 가장 필수적인 요소이다.

### Stack을 왜 쓸까?

1. 간단한 레이아웃 구성
: 복잡한 레이아웃을 간단하면서 직관적으로 구성할 수 있다.
2. 유연성
: 여러 스택을 중첩해서 사용할 수 있어서 더 다양한 레이아웃을 구성할 수 있다.
3. 가독성
: 깨끗한 코드를 유지하기 위해서 중요한 것은 바로 가독성. 스택을 사용하면 레이아웃 코드가 더 깔끔하고 가독성이 높아진다.

# Stack의 종류를 알아보자.

## VStack

<img src="https://github.com/user-attachments/assets/bb3bf524-2917-4796-b5c0-052a6ed19771" width="50%" height="50%">

<br>
<br>

VStack은 Vertical Stack의 약자로, 수직으로 쌓아 올리는 방식을 말한다. 즉, VStack 안에 있는 요소들은
수직으로 배치된다.

아래 예시 코드를 활용했을 때

```swift
VStack {
  Text("Hello, World!")
  Text("This is VStack.")
}
```

<img src="https://github.com/user-attachments/assets/41be3bb1-6cd1-4497-a689-db3e7025671e" width="50%" height="50%">

실제 화면에는 이렇게 구현이 될 것이다.

## HStack

<img src="https://github.com/user-attachments/assets/a0e22b70-d922-434e-8a4c-8be70097913b" width="50%" height="50%">

<br>
<br>

HStack은 Horizontal Stack의 약자로, 수평으로 배열하는 방식을 말한다. 즉, HStack 안에 있는 요소들은 
수평으로 배치된다.

아래 예시 코드를 활용했을 때

```swift
HStack {
  Text("Hello, World!")
  Text("This is HStack.")
}
```

<img src="https://github.com/user-attachments/assets/9ba1390c-abfd-4182-a215-8f057fbd3c50" width="50%" height="50%">

실제 화면에는 이렇게 구현이 될 것이다.

## ZStack

<img src="https://github.com/user-attachments/assets/ce5febf2-d8ce-4a9e-80f6-db6671d7a21e" width="50%" height="50%">

ZStack은 깊이를 가지고 배열하는 방식을 말한다. 즉, ZStack 안에 있는 요소들은 깊이 순서대로 배치가 된다.
따라서 뷰 위에 다른 뷰를 겹쳐서 표현할 수 있다.

아래 예시 코드를 활용했을 때

```swift
ZStack {
  Text("Hello, World!")
  Text("This is ZStack")
}
```

![image](https://github.com/user-attachments/assets/605f7491-bcec-4e0c-9c61-0aefd844e385)

실제 화면에는 이렇게 구현이 될 것이다.
