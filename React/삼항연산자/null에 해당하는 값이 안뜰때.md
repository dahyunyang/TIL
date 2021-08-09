문제) 닉네임의 중복 검사를 하는데, 따로 닉네임 인풋에 값을 적지 않아도 화면에 "사용가능한 닉네임입니다" 텍스트가 뜬다.


![스크린샷 2021-08-09 오후 2 56 05](https://user-images.githubusercontent.com/85469681/128677284-5aa90e52-f1ec-481f-a715-6d7907ce7467.png)

해결) user 모듈스에 initialState를 false -> null로 바꿔준다. 계속 false값만 떴기 때문에 false상태일때 해당하는 조건문이 발생함
![스크린샷 2021-08-09 오후 2 56 40](https://user-images.githubusercontent.com/85469681/128677545-4baf4867-c900-4e92-9721-51a87b4eba7a.png)

