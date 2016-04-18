---
layout: post
title: XCode의 playground를 이용하여 Swift 학습하기, 터미널(terminal)을 통해 swift 코드 실행시키기
---

<span class="italics"> 이 글은 OS X, El Capitan, Swift 2.2 환경에서 작성되었습니다.</span>

최근 동아리가 출전한 pCTF 2016에서 Swift언어로 된 문제가 출제되었다.  
아무래도 최근 구글이 Go는 서버 개발 위주로 활용하고 안드로이드 등에 Swift를 활용하는 것을 고려중이라는 소문이 돈 것이 반영된 듯 하다.  
Go 배우기도 바빴던 동아리원들에게 갑자기 Swift로 태세전환이라니 허탈감이 들지 않을 수가 없다.  
그래도 Swift는 애플에서 하도 홍보를 해서 흥미가 있었던 언어이기도 했고, 마침 또 중간고사 시험기간이라서 갑자기 Swift에 대한 호기심이 차올라 배워보기로 했다.

Swift가 최근에 Open-Source로 공개되긴 했지만, 역시 애플에서 만든 언어인 만큼 XCode에서 제대로 쓸 수 있을 것이다.
XCode를 실행하면 다음과 같은 화면이 나온다.
<p align="CENTER">
  <img src="{{ site.baseurl }}/images/Learning-Swift/Start_Swift.png" style="width: 640px;">
</p>

여기서 `Get started with a playground`를 눌러주자. 그러면 다음과 같은 화면이 나타난다.
<p align="CENTER">
  <img src="{{ site.baseurl }}/images/Learning-Swift/Playground.png" style="width: 640px;">
  <span class="italics">Playground의 모습. 안에 쓰여 있는 코드는 본인이 임의로 작성한 것이다.</span>
</p>

Playground에 적힌 모든 Swift 코드는 실시간으로 컴파일되어 실행되며, 그 결과값이 오른쪽과 아래에 나타난다. 직관적이므로 몇 번 타이핑해보면 쉽게 이해할 수 있다.
한 줄 한 줄 빠르게 실행이 되길래 python과 같은 interpreter언어인 줄 알았는데, Obj-C처럼 기계어로 compile한다고 한다. 뒤에서 설명하겠지만, 터미널에서 swift source.swift 명령어를 이용하여 소스 파일을 실행시킬 수 있는데, 이것도 python 등의 interpreter언어와 유사하다. 신기한 언어인 것 같다.

문법은 좀 더 깊게 배워봐야 알겠지만 전반적으로 python과 C 계통의 언어를 적당히 짬뽕한 느낌이다.  
보통 C 계열에서 영향을 받은 언어들은 변수를 선언할 때 int, char, ... 등등을 사용하는데 Swift는 조금 다르다.  
상수를 선언할 때는 `let` 키워드를 사용하며, 변수를 선언할 때는 `var` 키워드를 사용한다.

```Swift
let constInt = 20
var variables = 30
var doublePi = 3.14
let str = "IamString"
```

이렇게 선언할 수 있으며, 문장의 끝에 세미콜론(;)은 찍어도 되고, 찍지 않아도 된다.

이렇게 상수나 변수를 선언할 때, 특정 타입을 명시하여 선언할 수도 있으며, 이는 다음과 같이 하면 된다.

```Swift
var testString : String
```

`Double()` 등을 통해 서로 간에 형변환을 할 수도 있다.

이제 Hello, World!를 출력해 보자. Swift에서는 `print()` 함수가 stdout을 담당한다.

```Swift
print("Hello, World!")
```

위의 코드를 입력하면 왼쪽과 아래쪽의 창에 "Hello, World!"가 나타날 것이다.

Swift에서 `for`문을 선언하는 방법은 다음과 같다.

```Swift
for i in 1..<10 {
}
```

python의 `for i in range(1, 10)`과 같은 기능을 실행한다. 개인적으로는 저 ..< 기호가 맘에 들지 않지만, 쓰다 보면 익숙해져서 못 느낄지도 모른다.

`print()` 함수와 `for`문을 적당히 사용하여 구구단을 출력하는 코드를 작성해 보았다.

```Swift
for i in 1..<10 {
    for j in 1..<10 {
        var temp = i * j
        print(i, "*", j, "=", temp)
    }
}
```

이제 stdin을 통하여 입력에 따라 출력값이 변하는 코드를 짜 보려고 했지만, playground에서는 stdin을 지원하지 않는 것 같다. 그래서 터미널을 통해 standard input을 받아보기로 했다.

터미널을 열어서 swift를 입력했더니 다음과 같은 에러 메시지가 표시되었다.

<p align="CENTER">
  <img src="{{ site.baseurl }}images/Learning-Swift/Error_Msg.png" style="width: 640px">
  <span class="italics">module six가 없다는 에러 메시지가 표시된다.</span>
</p>

이는 `brew install python` -- `brew link python` -- `sudo easy_install pip` -- `pip install six` 의 커맨드를 순서대로 입력하여 해결할 수 있었다.

이후 다시 swift를 터미널에 입력하면 다음과 같이 swift가 실행된다.

<p align="CENTER">
  <img src="{{ site.baseurl }}images/Learning-Swift/Launched_Swift.png" style="width: 640px">
  <span class="italics">Swift가 정상적으로 실행된 모습.</span>
</p>

여기서 python처럼 코드를 직접 타이핑할 수도 있지만, 소스 파일을 따로 만들어서 실행해 보기로 결정하였다.
`:quit`를 입력하여 Swift를 종료한 후, vim을 통해 SwiftTest.swift 파일을 만들어 다음과 같이 입력하였다.

```Swift
print("What is your name?")
let name = readLine(stripNewline: true)
print("Your name is", name!)
```

3번째 줄에서 name 뒤에 !가 붙은 이유는 Swift만의 자료형인 Optional이 같이 출력되는 것을 막기 위해서인데. 이는 나중에 기회가 되면 설명하겠다.

```Swift
print("Your name is \(name!)")
```

위 코드 또한 같은 결과를 출력한다. C언어의 %d, %s, ... 등등의 Format String 개념이라고 보면 되겠다.
이를 저장한 후, `swift SwiftTest.swift`를 입력하면 코드가 실행된다.

<p align="CENTER">
  <img src="{{ site.baseurl }}images/Learning-Swift/Result.png" style="width: 640px">
  <span class="italics">입력한 String이 정상적으로 출력되는 것을 확인할 수 있다.</span>
</p>
