# TextEditor

TextEditor는 긴 텍스트를 표시하고 편집할 수 있는 뷰이다.
UI에서 스크롤 가능한 여러 줄의 텍스트를 표시하고 편집할 수 있다.

## 기본 구조

<br>

```swift
struct TextEditorView: View {
  @State private var editText: String = "입력해요!"

  var body: some View {
    TextEditor(text: $editText)
  }
}
```
<br>

기존에 언급한 스타일 커스텀들이 겹치는 부분이 많아서 생략함!

참고로 TextEditor는 불편한 점이 너무 많다. 
사용을 하다 보면 생각보다 이런 기능도 지원하지 않아서 저절로... TextField로 커스텀을 하게 될 것이다...
