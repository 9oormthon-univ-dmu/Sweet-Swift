# ActionSheet -> .confirmationDialog

액션 시트는 사용자가 한 액션에 대한 응답으로 두 개 이상의 옵션 중에서 선택하도록 할 때 사용한다.

<img width="285" alt="image" src="https://github.com/user-attachments/assets/e8ca3c60-9616-42ea-bdfb-31f90e97df7d">

앞서 학습한 alert처럼 액션시트 또한 deprecated되었다. 

<img width="618" alt="image" src="https://github.com/user-attachments/assets/d686a023-9159-4829-8f82-98d344aa8611">

그래서 이 액션시트를 대체하기 위해서는 `confirmationDialog()`라는 모디파이어를 사용한다.

## 기본 구조

```swift
@State var showingSheet = false
    
var body: some View {
  Button("Action Sheet 사용하기"){
    self.showingSheet.toggle()
  }
  .confirmationDialog("타이틀", isPresented: $showingSheet){
    Button("제거", role: .destructive) {}
    Button("취소", role: .cancel) {}
  }
}
```

여기서 제목이나 메시지를 추가하고 싶다면?

```swift
.confirmationDialog(
    "타이틀",
    isPresented: $showingSheet,
    titleVisibility: .visible
  ){
    Button("제거", role: .destructive) {}
    Button("취소", role: .cancel) {}
  } message: {
    Text("메시지 추가")
  }
```

이렇게 `titleVisibility`를 통해 설정한 후, message를 추가할 수 있다.

<img width="289" alt="image" src="https://github.com/user-attachments/assets/f8414a60-2e6f-43cf-8078-b50be8d87d6d">
