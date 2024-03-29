# iOS

 https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/iOS

### 1. App Life Cycle
### 2. View Life Cycle
### 3. Delegate vs Block vs Notification
### 4. Memory Management
### 5. assign vs weak
### 6. Frame vs Bounds
### 7. protocol
### 8. Etc
- Bounds 와 Frame 의 차이점을 설명하시오.
: Bounds는 화면 기준으로 x,y의 좌표값이고, Frame은 자신이 속한 부모를 기준으로 한 x,y의 좌표값이다.

- 실제 디바이스가 없을 경우 개발 환경에서 할 수 있는 것과 없는 것을 설명하시오.
  : 시뮬레이터로 한다. 
    - 할 수 없는 것 : 카메라 촬영, 통화기능, sms 기능, 앱스토어
    - 할 수 있는 것 : iCloud, iMessege, 음성메세지, GPS

- 앱의 실행 단계

: [Life-Cycle](https://velog.io/@cskim/iOS-App-생명주기Life-Cycle)

<img src="./Image/appcycle.png" alt="AppCycle" style="zoom: 33%;" />

`UIApplication` :  SingleTone, event Loop를 관리, 중요 이벤트나 app 상태변화 등을 AppDelegate에 전달

`AppDelegate` : SingleTone, `UIApplication` 로부터 app life cycle 동안 앱  상태 변화에 따른 커스텀 코드 처리를 위임 받은 클래스,  `UIApplicationDelegate` protocol을 구현해서 처리

1. `UIApplication` 객체 생성
2. `@UIApplicationMain` 이 있는 class `AppDelegate`를 찾아서 생성
3. `UIApplication` 객체는 `info.plist` 파일을 바탕으로 앱에 필요한 데이터와 객체를 로드
4. 주요 객체 생성, Main Event Loop (유저 액션을 받는 루프) 생성 등 실행 준비. 끝나기 직전에 `application(_:willFinishLaunchingWithOptions:)` 호출
5. 준비가 끝나고 앱이 실행되기 직전에 `application(_:didFinishLaunchingWithOptions:)` 호출
6. Main run loop 실행. 사용자로부터 받은 event를 event queue를 통해 순서대로 처리. 이벤트 핸들(@IBOutlet, @IBAction 등)에 의해 커스텀 코드와 연결되어 실행시킴
7. App을 더 이상 사용하지 않으면 iOS system에 terminate 메시지 전달, `applicationWillTerminate(_:)` 호출.
8. App 종료



- 앱이 foreground에 있을 때와 background에 있을 때 어떤 제약사항이 있고, 상태 변화에 따라 다른 동작을 처리하기 위한 델리게이트 메서드들을 설명하시오.

    <img src="./Image/viewcycle.png" alt="Method" style="zoom: 33%;" />

    - background에 있을 때 제약사항

        : 드로잉 관련 명령어를 수행하면 안된다. (앱이 종료됨)

        : 소켓 연결이 모두 끊긴다.

        : foreground보다 자원 우선순위에서 밀려서 상태가 날아가거나 공유자원에 접근했을 때 앱이 강제 종료됨.

        : alert, action sheet 등 알람 뷰를 내려줘야한다.

        : 뷰 위의 민감한 정보를 지워야한다. -> 백그라운드로 전환될때 시스템이 메인 윈도우를 스냅샷으로 저장하는데, foreground로 다시 전환 될때 그 스냅샷을 잠깐 다시 보여주기 때문에

        : 작업 가능 시간이 길면 안됨 -> 길어지면 시스템이 앱을 종료시켜버림

    

    (앱의 상태)

    - Not Running (앱이 실행되지 않은 상태)
    - Foreground
      - Active (앱이 실행중이며 이벤트가 발생한 상태) 
      - Inactive (앱이 실행중이나 이벤트를 받지 않는 상태) - 알림이 떴을때, 시스템 메세지, 전화 알림 등등
    - Background
      - Background (앱이 백그라운드에 있으나 실행되는 코드가 있는 상태) - 홈버튼 눌러서 내리기
      - Suspend (앱이 백그라운드에 있고, 실행되는 코드가 없는 상태) - 일정한 이유에따라 background에서 실행되는 걸 OS가 상태를 변경시킨다.

    

    (앱의 상태에 따른 Delegate) - UIApplicationDelegate의 메서드 중

    - application(:didFinishLaunching) - 앱이 처음 실행할때
    - applicationWillResignActive - Active -> Inactive 되었을때
    - applicationDidEnterBackground - 앱이 Background가 되었을때 (중요 데이터 저장, 공유자원 해제)
    - applicationWillEnterForeground - Background -> Foreground (아직 foreground에서 실행되지는 않음)
    - applicationDidBecomeActive - 앱이 Active 되었을때
    - applicationWillTerminate - 앱이 종료(Not Running)될때

<img src="./Image/allcycle.png" alt="Cycle" style="zoom:33%;" />



- scene delegate에 대해 설명하시오.

    : 




- NSOperationQueue 와 GCD Queue 의 차이점을 설명하시오.

  : 




- GCD API 동작 방식과 필요성에 대해 설명하시오.

  : 




- 자신만의 Custom View를 만들려면 어떻게 해야하는지 설명하시오.

  : 




- iOS 앱을 만들고, User Interface를 구성하는 데 필수적인 프레임워크 이름은 무엇인가?

  : UIKit




- Foundation Kit은 무엇이고 포함되어 있는 클래스들은 어떤 것이 있는지 설명하시오.

  : 기본 연산 라이브러리 , Math, Codable 등등




- Delegate란 무언인가 설명하고, retain(유지하다) 되는지 안되는지 그 이유를 함께 설명하시오.

  : 




- NotificationCenter 동작 방식과 활용 방안에 대해 설명하시오.

  : 




- UIKit 클래스들을 다룰 때 꼭 처리해야하는 애플리케이션 쓰레드 이름은 무엇인가?

  : Main Thread




- TableView를 동작 방식과 화면에 Cell을 출력하기 위해 최소한 구현해야 하는 DataSource 메서드를 설명하시오.

  : 테이블뷰가 스크롤하기 전에 새롭게 보여져야 할 몇개의 메모리 자원에 할당해놓고 해당 메모리를 계속해서 재사용한다.


  - tableView(:row) - cell 갯수
  - tableView(:) -> UITableViewCell - cell 인스턴스를 반환하는 delegate




- 하나의 View Controller 코드에서 여러 TableView Controller 역할을 해야 할 경우 어떻게 구분해서 구현해야 하는지 설명하시오.

: 하나의 목적을 가진 코드끼리 묶어 메서드로 분리한다. Ex) sendEmail (email을 보내는 코드끼리)




- App Bundle의 구조와 역할에 대해 설명하시오.

  : 앱 바이너리, 리소스 파일 등을 포함한 파일. 지원하는 모든 디바이스에 대한 데이터를 가지고 있다.

  ```
  MyApp.app
     MyApp : (필수) 응용프로그램 코드가 포함된 실행파일
     MyAppIcon.png 
     MySearchIcon.png
     MySettingsIcon.png : (필수/권장) 앱 아이콘
     Info.plist : (필수) bunddle ID, 버전 넘버 및 display name 등 응용프로그램 구성 정보
     Default.png : (권장) 앱 윈도우가 로드되기 전까지의 임시 이미지 없으면 검은색 화면
     MainWindow.nib : (권장) 앱 시작시 로드할 기본 인터페이스 개체
     Settings.bundle : 설정 앱에 추가하는 앱 별 환경설정을 추가하는 플러그인
     iTunesArtwork
     en.lproj
        MyImage.png
     fr.lproj
        MyImage.png : 사용자 정의 리소스 파일
  ```

  


- View 객체에 대해 설명하시오.

  : 

  


- UIView 에서 Layer 객체는 무엇이고 어떤 역할을 담당하는지 설명하시오.

  :

  


- UIWindow 객체의 역할은 무엇인가?

  :

  


- UINavigationController 의 역할이 무엇인지 설명하시오.

  :

  


- 모든 View Controller 객체의 상위 클래스는 무엇이고 그 역할은 무엇인가?

  :

  


- 앱이 시작할 때 main.c 에 있는 UIApplicationMain 함수에 의해서 생성되는 객체는 무엇인가?

  :

  


- UIApplication 객체의 컨트롤러 역할은 어디에 구현해야 하는가?

  :

  


- 앱의 콘텐츠나 데이터 자체를 저장/보관하는 특별한 객체를 무엇이라고 하는가?

  :

  


- 앱 화면의 콘텐츠를 표시하는 로직과 관리를 담당하는 객체를 무엇이라고 하는가?

  :

  


- Swift의 클로저와 Objective-C의 블록은 어떤 차이가 있는가?

  :

  


- App의 Not running, Inactive, Active, Background, Suspended에 대해 설명하시오.

  :

  


- App thinning에 대해서 설명하시오.

  :

  


- Global DispatchQueue 의 Qos 에는 어떤 종류가 있는지, 각각 어떤 의미인지 설명하시오.

  :



## Autolayout
- 오토레이아웃을 코드로 작성하는 방법은 무엇인가? (3가지)

  :

  


- hugging, resistance에 대해서 설명하시오.

  :

  


- Intrinsic Size에 대해서 설명하시오.

  :

  


- 스토리보드를 이용했을때의 장단점을 설명하시오.

  :

  


- Safearea에 대해서 설명하시오.

  :

  


- Left Constraint 와 Leading Constraint 의 차이점을 설명하시오.

  :



## Swift
- Optional 이란 무엇인지 설명하시오.

  :

  


- Fast Enumration 이란 무엇인지 설명하시오. 

  :

  


- Struct 가 무엇이고 어떻게 사용하는지 설명하시오.

  :

  


- instance 메서드와 class 메서드의 차이점을 설명하시오.

  :

  


- Delegate 패턴을 활용하는 경우를 예를 들어 설명하시오.

  :

  


- Singleton 패턴을 활용하는 경우를 예를 들어 설명하시오.

  :

  


- KVO 동작 방식에 대해 설명하시오.

  :

  


- Delegates와 Notification 방식의 차이점에 대해 설명하시오.

  :

  


- 멀티 쓰레드로 동작하는 앱을 작성하고 싶을 때 고려할 수 있는 방식들을 설명하시오.

  :

  


- MVC 구조에 대해 블록 그림을 그리고, 각 역할과 흐름을 설명하시오.

  :

  


- 프로토콜이란 무엇인지 설명하시오.

  :

  


- Hashable이 무엇이고, Equatable을 왜 상속해야 하는지 설명하시오.

  :

  


- mutating 키워드에 대해 설명하시오.

  :

  


- 탈출 클로저에 대하여 설명하시오.

  :

  


- Extension에 대해 설명하시오.

  :

  


- 접근 제어자의 종류엔 어떤게 있는지 설명하시오

  :

  


- defer란 무엇인지 설명하시오.

  :

  


- defer가 호출되는 순서는 어떻게 되고, defer가 호출되지 않는 경우를 설명하시오.

  :



## ARC
- ARC란 무엇인지 설명하시오.

  :

  


- Retain Count 방식에 대해 설명하시오.

  :

  


- Strong 과 Weak 참조 방식에 대해 설명하시오.

  :

  


- ARC 대신 Manual Reference Count 방식으로 구현할 때 꼭 사용해야 하는 메서드들을 쓰고 역할을 설명하시오.

  :

  


- retain 과 assign 의 차이점을 설명하시오.

  :

  


- 순환 참조에 대하여 설명하시오.

  :

  


- 강한 순환 참조 (Strong Reference Cycle) 는 어떤 경우에 발생하는지 설명하시오.

  :

  


- 특정 객체를 autorelease 하기 위해 필요한 사항과 과정을 설명하시오.

  :

  


- Autorelease Pool을 사용해야 하는 상황을 두 가지 이상 예로 들어 설명하시오. 

  :

  


- 다음 코드를 실행하면 어떤 일이 발생할까 추측해서 설명하시오.
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];



## Functional Programming
- 함수형 프로그래밍이 무엇인지 설명하시오.

  :

  


- 고차 함수가 무엇인지 설명하시오.

  :

  


- Swift Standard Library의 map, filter, reduce, compactMap, flatMap에 대하여 설명하시오.

  :



## Architecture
- 의존성 주입에 대하여 설명하시오.

  :

  

- MVC에 대해 설명하시오.

  :

  


- MVVM에 대해 설명하시오.

  :

  


- RIBs에 대해 설명하시오.

  :



## Rx
- Reactive Programming이 무엇인지 설명하시오.

  :

  


- RxSwift에서 Hot Observable과 Cold Observable의 차이를 설명하시오.

  :


