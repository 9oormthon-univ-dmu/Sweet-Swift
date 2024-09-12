# Picker

피커는 값의 집합에서 선택하기 위한 컨트롤러이다.

## 기본 구조

```swift
enum Flavor: String, CaseIterable, Identifiable {
  case chocolate, vanilla, strawberry
  var id: Self { self }
}

@State private var selectedFlavor: Flavor = .chocolate

var body: some View {
  List {
    Picker(selection: $selectedFlavor) {
      Text("Chocolate").tag(Flavor.chocolate)
      Text("Vanilla").tag(Flaver.vanilla)
      Text("Strawberry").tag(Flavor.strawberry)
    } label: {
      Text("Flavor")
      Text("Choose your favorite flavor")
    }
  }
}

// enum 대신 배열과 ForEach를 통해 나열할 수도 있다.
```

#### 결과 화면

<img width="283" alt="image" src="https://github.com/user-attachments/assets/ad288b26-dee7-4a6e-8e94-b49e1b9554f4">

## Picker 스타일 옵션

#### `DefaultPickerStyle`

선택기의 기본 스타일

<img width="186" alt="image" src="https://github.com/user-attachments/assets/cbeda8e7-08f1-4c16-8070-431e06a412e0">

#### `WheelPickerStyle`

스크롤 가능한 휠에 옵션을 표시하는 스타일

<img width="190" alt="image" src="https://github.com/user-attachments/assets/68fd2c9f-aeb8-473d-96fa-f427ea5d2780">

#### `SegmentedPicker`

세그먼트화 된 컨트롤에서 옵션을 제공하는 스타일

<img width="196" alt="image" src="https://github.com/user-attachments/assets/102e3486-6dd8-4bb8-9253-b5e3b75a8f20">

이외에도 NavigationView를 연결해서 새로운 선택 화면을 만들거나, Section을 사용하는 등 여러가지 활용 방법이 있다.

<br><br>

# DatePicker

날짜를 선택하기 위한 컨트롤러이다.

<img width="164" alt="image" src="https://github.com/user-attachments/assets/5b3dde06-2b71-4ec5-9f7d-42c0377fcacc">

<img width="192" alt="image" src="https://github.com/user-attachments/assets/d28f83d1-69f0-4a00-b1c7-89b854e5a08f">


## 기본 구조

```swift
@State private var date = Date()

var body: some View {
  DatePicker(
    "Start Date",
    selection: $date,
    displayedComponents: [.date]
  )
}
```

## DatePicker 스타일 옵션

#### `displayComponents`

- `.date` : 월/일/년
- `.hourAndMinute` : 시간

#### `.datePickerStyle()`

- `DetaultDatePickerStyle()` & `CompactDatePickerStyle()` : 기본 선택기
- `GraphicaldatePickerStyle()` : 정확한 시간을 입력할 수있는 달력 표시하는 고급 날짜 선택기
- `WheelDatePickerStyle()` : 휠을 통해 날짜나 시간을 표시하는 선택기

또한, 데이트피커 옆에 붙는 레이블 텍스트를 안 보이게 하려면 `.labelHidden()` 모디파이어를 활용할 수 있다.

<br><br>

# ColorPicker

시스템 색상 선택기 UI에서 색상을 선택하는데 사용되는 컨트롤러이다.

<img width="290" alt="image" src="https://github.com/user-attachments/assets/659d1384-700f-4714-a13a-0380c7f04136">

## 기본 구조

```swift
@State private var bgColor = Color.white

var body: some View {
  VStack {
    ColorPicker("배경색 선택", selection: $bgColor)
  }
  .background(bgColor)
}
```

## Color 지정 방법

1. Color.색상명 : 기본 에셋 색상
2. Color(.sRGB, red: Double, green: Double, blue: Double, opacity: Double = 1)

<br><br>

# Stepper

증가 또는 감소 동작을 수행하는 컨트롤러이다. 화면에서는 + 와 - 버튼으로 구성된 것이 바로 Stepper이다.

## 기본 구조

```swift
@State private var count = 0.0

var body: some View {
  Stepper(value: $count) {
    Text("\(Int(count))개")
  }
}

// 증감률 제한 방법
Stepper(value: $someValue, in: n...nn)

// 원하는 증감 단위 설정 방법
Stepper(value: $someValue, in: n...nn, step: 0.5)

// 기본 소수점 없애는 방법
Text("\(value, specifier: "%g"))")

```

#### 결과 화면

<img width="283" alt="image" src="https://github.com/user-attachments/assets/0ed58db5-93e3-41ef-8bb5-f697eb100eff">

