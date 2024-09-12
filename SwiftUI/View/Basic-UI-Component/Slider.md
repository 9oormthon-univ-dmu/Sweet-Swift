# Slider

슬라이더는 제한된 선형 범위의 값에서 값을 선택하기 위한 컨트롤이다.
선형 트랙의 끝 값들은 최소 및 최대 값을 나타내며, 사용자가 엄지를 움직이면 슬라이더는 바인딩된 값을 업데이트한다.

<img width="432" alt="image" src="https://github.com/user-attachments/assets/9a90e3a6-1771-442a-81e5-6255e15253ee">

## 기본 구조

슬라이더의 기본 구조는 아래 코드와 같다.

<br>

```swift
@State private var speed = 50.0
@State private var isEditing = false

var body: some View {
  VStack {
    Slider(
      value: $speed,
      in: 0...100,
      step: 5,
      onEditingChanged: { editing in
        isEditing = editing
      }
    )
    .accentColor(.orange)

    Text("\(Int(speed))")
      .foregroundColor(isEditing ? .red : .blue)
  }
}
```

<br>

여기서 가장 중요한 것은 슬라이더에 포함된 매개변수이다.

- `value` : What Double to bind it to
- `in` : 슬라이더의 범위
- `step` : 슬라이더를 이동할 때 값을 변경하는 정도

부가적으로 슬라이더에 컬러를 추가할 때는 `.accentColor(ColorName)` 모디파이어를 활용하여 변경할 수 있다.

<br>

또한 슬라이더에는 value가 무조건 Double이기 때문에 실제 Text로 보여줬을 때 소수점이 길게 나와서 가독성이 떨어져 보이기도 한다.
그래서 보통은 `\(Int(value))`를 통해 형변환을 하거나, `\(value, specifier: "%.2f")`처럼 소수점 자리수를 설정할 수 있다.
