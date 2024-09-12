# Alert

Alert는 경고메시지를 표시하는 것이다.

여기서 애플 공식 문서에 Alert을 검색하면

<img width="592" alt="image" src="https://github.com/user-attachments/assets/2a5dbfc2-2b88-4beb-9286-a3e00d2a0bb3">

Alert이라는 뷰는 사라졌고 대신 모디파이어로 대체된다는 사실을 알 수 있다.
물론 사라졌다는 말은 아니고 iOS 이전 버전에서는 기존의 Alert() 뷰를 사용하지만 현재 iOS 15 이상부터는 `.alert`라는 모디파이어를 사용한다고 이해하면 된다.

## 기본 구조

<br>

```swift
// 기본
@State private var showingAlert = false

var body: some View {
  Button("알림") {
    self.showingAlert.toggle()
  }
  .alert("Title", isPresented: $showingAlert){
    Button("OK"){}
  } message: {
    Text("message")
  }
}

// 취소 버튼 역할
.alert("Title", isPresented: $showingAlert){
    Button("Cancel", role: .cancel){}
  } message: {
    Text("message")
  }

// Destructive 버튼 역할
//: 굉장히 위험하거나 치명적인 혹은 되돌리기 힘든 일을 함을 명시적으로 표현하기 위한 빨간색 버튼과 취소 버튼이 자동으로 생김
// 생각을 해보니 "나가기" "종료" 이런 내용의 알림창일 때 그런 모양이었던 것 같다.
.alert("Title", isPresented: $showingAlert){
    Button("Destruct", role: .destructive){}
  } message: {
    Text("message")
  }

```

<br>

이렇게 기본 구조를 사용해보면

<img width="244" alt="image" src="https://github.com/user-attachments/assets/ed4823b8-7c13-4a53-acc1-9306b9eebe05">

결과는 이렇게 알림창이 뜨게 된다.

<br>

아까 좀 새로웠던 Destructive 역할을 부여하면

<img width="230" alt="image" src="https://github.com/user-attachments/assets/48f4443d-be3d-4df5-b4f3-b5b714aacc8b">

결과는 이렇다.

<br>

```swift
.alert("Title", isPresented: $showingAlert){
    Button("OK"){}
    Button("How"){}
    Button("Destruct", role: .destructive){}
  } message: {
    Text("message")
  }
```

해당 코드를 통해 많은 버튼을 알림창에 추가할 수 있다.

<img width="232" alt="image" src="https://github.com/user-attachments/assets/89a5c988-02f9-4307-9ffa-704c6c05f22a">

