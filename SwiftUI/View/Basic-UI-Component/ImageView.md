# Image

이미지 뷰는 이미지를 화면에 표시하는 데 사용된다.
로컬 파일이나 URL을 통해 이미지를 불러올 수 있고, 다양한 모디파이어를 통해 이미지를 커스텀할 수 있다.

## 기본 구조

<br>

```swift
// 로컬 이미지 파일 표시
Image("이미지 이름")

// 시스템 이미지 파일 표시: SF Symbols 애플리케이션을 통해 이름 찾기 쉬움
Image(systemName: "star.fill")
```

<br>

## 크기 조정

이미지 크기를 조정하게 되면 `.resizable()` 모디파이어를 사용한 후에 `frame` 모디파이어로 이미지 크기를 조정할 수 있다.

<br>

```swift
Image("이미지 이름")
  .resizable()
  .frame(width: 100, height: 100)
```

<br>

## 이미지 비율 유지

이미지 사이즈를 조정하다 보면 원본 비율이 깨지기도 한다. 그래서 이 비율을 유지하려면 `.aspectRatio` 모디파이어를 사용해야 한다.

- `.fill`: 주어진 프레임에 이미지를 맞추고, 넘치는 부분을 잘라낸다.
- `.fit` : 주어진 프레임에 이미지를 맞추고, 비율을 유지한다.

<br>

```swift
Image("이미지 이름")
  .resizable()
  .aspectRatio(contentMode: .fit)
  .frame(width: 100, height: 100)
```

<br>

## 클리핑 및 마스킹

이미지를 특정 모양으로 자르거나 마스킹할 수 있다. `.clipShape()` 모디파이어를 사용하여 원, 사각형 등으로 이미지를 자를 수 있다.

<br>

```swift
Image("이미지 이름")
  .resizable()
  .frame(width: 100, height: 100)
  .clipShape(Circle())
```

<br>

## 테두리 추가

이미지에 테두리를 추가하려면 `.overlay()` 모디파이어를 사용하여 테두리를 만들 수 있다.

<br>

```swift
Image("이미지 이름")
  .resizable()
  .frame(width: 100, height: 100)
  .overlay(Circle().stroke(Color.blue, lineWidth: 4))
```

<br>

매번 강조하지만!! 모디파이어 적용하는 순서가 정말 중요하니까 순서!! 명심하기
