# Text

SwiftUI에서 문자열을 화면에 표시하는 가장 기본적인 뷰가 바로 Text 뷰 이다.
UIkit의 UILabel과 비교했을 때, 단순히 문자열 처리만 해주는게 아니라 버튼이나 다른 UI에 구성되는 텍스트들 모두 Text가 적용한다.
다양한 텍스트 스타일부터 속성을 사용해서 스타일을 적용하는 방법까지 학습한다.

## 기본 구조

텍스트 뷰는 Text 구조체를 통해 생성된다. 가장 간단한 방법은 아래 코드처럼 입력하면 화면에 텍스트가 출력될 것이다.

<br>

```swift
Text("텍스트 입력")

Text("Hello, SwiftUI World!")
```
<br>

## 스타일

여러 모디파이어를 통해 스타일을 지정할 수 있다. 폰트 크기부터 색상, 굵기 등을 설정할 수 있다.

#### 폰트 스타일

|옵션|내용|
|---|---|
|largeTitle|큰 제목 폰트|
|title|제목 폰트|
|headline|헤드라인 폰트|
|subheadline|서브헤드라인 폰트|
|body|본문 폰트|
|callout|콜아웃 폰트|
|footnote|각주 폰트|
|caption|캡션 폰트|

<br>

```swift
Text("Hi!")
  .font(.headline)
```

<br>

만약 기본 값이 아닌 다른 폰트를 커스텀하고 싶다면 해당 폰트를 다운로드한 후 Resource 파일에 추가한 후 Info.plist 파일 내부에 `FONTS PROVIDED BY APPLICATION`을 추가한 후 폰트 파일을 추가해야 한다.

이 세팅이 모두 끝났다면 아래 코드를 Extension으로 추가해주면 기본 폰트 스타일처럼 적용할 수 있다.

<br>

```swift

//Font.swift
extension Font {
  static let pretendardBold18: Font = .custom("Pretendard-Bold", size: 18)

  // 필요한 폰트를 모두 extension
  ...
}

// 폰트 적용
Text("Hi")
  .font(.pretendardBold18)
```

<br>

#### 색상 스타일

텍스트의 색상은 `foregroundColor` 모디파이어를 통해 변경할 수 있다.

<br>

```swift
// 기본 색상 적용
Text("Hi!")
  .foregroundColor(.blue)

// 사용자 정의 색상 적용
Text("Hi!")
  .foregroundColor(Color(red: 0.5, green: 0.7, blue: 0.8))
```

<br>

색상도 extension에 추가해서 커스텀할 수 있는데, 먼저 `Assets.xcassets` 파일에 색상을 해시코드 값으로 등록한 후 아래 코드를 추가하면 사용할 수 있다.

<br>

```swift

// Color.swift
extension Color {
  static let Gray100 = Color("Gray100")
  static let Gray200 = Color("Gray200")
  ...
}

// 폰트 적용
Text("Hi")
  .foregroundColor(.Gray100)
```

<br>

#### 굵기 설정

기본 스타일에서는 텍스트 굵기를 설정하는 옵션들이 있다.

|옵션|내용|
|---|---|
|ultraLight|매우 얇게|
|thin|얇게|
|light|약간 얇게|
|regular|보통|
|medium|중간 굵기|
|semibold|약간 두껍게|
|bold|두껍게|
|heavy|매우 두껍게|
|black|가장 두껍게|

`fontWeight` 모디파이어를 통해 굵기를 적용할 수 있다.

<br>

```swift
Text("Hi")
  .fontWeight(.semibold)
```

<br>

#### 정렬

텍스트의 기본 정렬은 왼족 정렬이지만 + Stack에서 적용된 정렬을 따르지만 간혹 줄이 넘어가면 이상하게 정렬이 되는 경우가 있다.
그래서 이걸 방지하기 위해서는 `multilineTextAlignment` 모디파이어를 사용해 해결할 수 있다.

<br>

```swift

// 왼쪽 정렬
Text("Hi")
  .multilineTextAlignment(.leading)

// 중앙 정렬
Text("Hi")
  .multilineTextAlignment(.center)

// 오른쪽 정렬
Text("Hi")
  .multilineTextAlignment(.trailing)
```

<br>

#### 줄바꿈

텍스트가 길어질 때 줄 바꿈을 허용하거나, 최대 줄 수를 제한할 수 있다.

<br>

```swift
// 줄 바꿈 허용
Text("Hi")
  .lineLimit(nil)

//최대 줄 수 제한
Text("Hi")
  .lineLimit(3)
```

<br>

#### 여백

여백은 지난번 Stack에서도 언급했던 `padding`이라는 모디파이어에 값을 대입해 여백을 추가해줄 수 있다.
