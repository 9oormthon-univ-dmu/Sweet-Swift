# Modifier

| modifier(_:) : Applies a modifier to a view and returns a new view.

modifier()는 view에서 modifier를 적용해서 새로운 view를 만들어 리턴하는 것이다.
즉 view에 style을 추가하기 위한 메소드라고 이해하면 될 것이다.

modifier는 적용 순서에 따라서도 완전히 다른 뷰가 생성될 수 있다는 점을 유의할 필요가 있다.

### 크기 변경하기

#### `.frame()` : 뷰의 크기와 위치를 지정하는데 사용

```swift
func frame(
	width: CGFloat? = nil,
	height: CGFloat? = nil, 
	alignment: Alignment = .center
) -> some View

func frame(
	minWidth: CGFloat? = nil,
	idealWidth: CGFloat? = nil, 
	maxWidth: CGFloat? = nil, 
	minHeight: CGFloat? = nil, 
	idealHeight: CGFloat? = nil, 
	maxHeight: CGFloat? = nil, 
	alignment: Alignment = .center
) -> some View
```

예를 들어서 사용해보면

```swift
VStack {

...
}
.frame(width: 300, height: 300)
```

300 X 300 프레임의 수직정렬 Stack 이 생긴다.
(이때 background modifier를 함께 사용하게 될 경우 background를 먼저 선언한 후 frame을 선언해야 반영된다.)

### 정렬 방식 변경하기

각 Stack 안에는 정렬 방식을 변경하는 파라미터 값이 존재한다.

```swift
VStack(alignment: _) {
...
}
```

이 파라미터 값으로 정렬 방식을 변경해줄 수 있다.

|종류|정렬|
|---|---|
|VStack|`.trailing` `.leading` `.center`|
|HStack|`firstTextBaseline` `.center` `.bottom` `.top` `.lastTextBaseline`|
|ZStack|`.trailing` `.leading` `.topLeading` `.center` `.bottom` `.top` `.bottomLeading` `.bottomTrailing`|

Stack 종류에 따라서 정렬을 적용해주면 끝!

### 여백 크기 변경하기

각 Stack 안에는 여백 크기를 변경하는 파라미터 값이 존재한다.

```swift
VStack(spacing: _) {
...
}
```

이 파라미터 값에 여백 값을 따로 지정해줘야 한다. 여기서 spacing의 default 값은 0이 아니기 때문에 값을 꼭 입력할 필요가 있다.

#### `.padding()` : 뷰의 주위에 여백을 추가하는 데 사용

.padding()은 파라미터가 아닌 modifier로 상하좌우 여백을 설정해줄 수 있다.

예를 들어서 상하좌우 모두 여백을 10씩 주고 싶다면

```swift
VStack {

}
.padding(.all, 10)
```

이렇게 적용해줄 수 있다.

- `.top` : view 상단
- `.leading` : view 왼쪽
- `.bottom` : view 하단
- `.trailing` : view 오른쪽
- `.all` : 모든 면 (상하좌우)
- `.horizontal` : 수평 (좌우)
- `.vertical` : 수직 (상하)

#### `.edgesIgnoringSafeArea` : 화면의 안전 영역 밖으로 확장되도록 영역을 변경

디바이스의 전체 영역을 통해 view를 보여주고 싶을 때 사용되는 modifier이다.
주로 스플래시 화면을 보여줄 때 사용한다.

```swift
VStack {
 ...
}
.edgesIgnoringSafeArea(.all)
```




