[View Controller 생명주기]

1. viewDidLoad : View Controller가 메모리에 로드될때 호출. 
2. viewWillAppear : View Controller가 화면에 보이기 시작할 것이라고 알려줄 때.
3. viewDidAppear : View Controller가 화면에 나타났을때 호출.
4. viewWillDisappear : View Controller가 화면에서 사라질 것이라고 알려줄 때.
5. viewDidDisappear : View Controller가 화면에서 사라졌을때 호출.



예제)

- 특정 화면에 진입했을 때 로그인이나 권한 여부를 체크하고 싶을 때
- 화면이 표시될 때마다 최신 데이터로 업데이트해주고 싶을 때
- 메모리 부족 시 가용 메모리를 확보하는 코드를 작성하고 싶을 때, 메모리 부족 체크 하는 곳
- 화면이 완전히 표시되었는지 체크해서 알림창으로 공지를 띄워주고 싶을 때
- 사용자가 저장 버튼을 누르지 않아도 지금 화면 상태를 다음에도 유지하고 싶을 때


[APP 생명주기]
1. APP의 상태

Not Running : 앱이 시작되지 않거나 실행되었지만 시스템에 의해 종료된 상태
Inactice : 앱이 전면에서 실행 중, 아무런 이벤트를 받지 않는 상태
Active : 앱이 실행중, 이벤트를 받고 있는 상태
Background : 앱이 백그라운드에 있지만 여전히 코드가 실행되고 있는 상태 / 파일다운로드, 업로드, 연산 처리 등 여분의 실행 시간이 필요할때 사용
Suspended : 앱이 메모리에 유지되지만 실행되는 코드가 없는 상태 / 메모리가 부족한 상황이 오면 ios 시스템은 포그라운드에 있는 앱의 여유 메모리 공간확보를 위해
            특별한 알림 X
            
2. APP의 실행상태가 변화할 때  APP객체는 델리게이트에 정의된 특정 메소드를 호출


application(_:willFinishLaunchingWithOptions:)
-> 앱이 구동되어 필요한 초기 실행 과정이 완료되기 직전에 호출

application(_:didFinishLaunchingWithOptions:)
-> 앱이 사용자에게 표시되기 직전에 호출되는 메소드

applicationDidBecomeActive(_:)
-> 실행된 앱이 포그라운드, 화면에 표시될 때 호출되는 메소드. 

applicationDidEnterBackground(_:)
-> 앱이 백그라운드 상태에 진입했을때 호출. 공유 자원이 있다면 해제시키는 코드 작성.

applicationWillTerminate(_:)
-> 앱이 종료되기 직전에 호출되는 메소드.

