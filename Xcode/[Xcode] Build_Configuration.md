## Build Configuration 추가하기

사내 배포 시, configuration을 추가해주기 위해 추가
</br>
.xcodeproj > Project > Info > Configuration 에서
</br>
추가 버튼으로 config 값을 copy하고 싶은 configuration을 선택해서 추가 해준다
</br>

### 추가한 Configuration으로 배포 설정, Scheme 설정 
1. CD 사용하고 있는 툴에 해당 build configuration으로 설정 </br>
fastlane을 사용하고 있기 때문에 추가한 build configuration으로 출시할 lane 추가 </br>
2. Build Scheme 생성
3. ++ XCConfig를 이용하여 동일한 환경으로 만들 수 있음.

### 추가한 Configuration으로 전처리문 사용하기
해당 Build Configuration에 해당하는 서버 주소나, 기타 설정 값등을 바꿔주기 위해  </br>
전처리문을 사용하기위한 Flag 설정 </br>
</br>
1. .xcodeproj > builld settings > swift compiler - Custom Flags
2. Apple Clang - Preprocessing 에 해당 빌드시 사용하고 싶은 define 값을 전처리문 타입에 넣어준다.
</br>

</br>
Activie Compilation Conditions에 사용할 flag value를 넣어준다.


[참고]</br>
https://minsone.github.io/ios/mac/xcode-xcconfig</br>
https://zeddios.tistory.com/705</br>
https://eunjin3786.tistory.com/219</br>