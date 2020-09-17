# 주제 : 꽃 배달 

# 기능적 요구사항
- 고객이 꽃배달 메뉴 선택하여 주문한다
- 주문이 되면 결제 시스템의 결제 기능이 호출된다
- 결제가 완료되면 주문 내역이 꽃가게 주인에게 전달된다
- 꽃가게 주인이 주문을 확인하여 꽃을 만들어 배송을 시작한다
- 고객이 주문을 취소할 수 있다

- 배송이 완료되면 고객에게 리뷰 작성 요청을 한다
- 리뷰작성 요청이 되면 SMS를 
- 고객은 리뷰를 작성한다
- 주인은 작성된 리뷰를 확인한다 

- 주문이 취소되면 배송이 취소된다
- 고객이 주문상태를 조회한다
- 주문상태가 바뀔 때 SMS로 알림을 보낸다

# 이벤트스토밍
<img width="1825" alt="eventstorming" src="https://user-images.githubusercontent.com/29944530/93425063-39950e80-f8f4-11ea-8ab3-26806c81329e.png">


<img width="1177" alt="스크린샷 2020-09-17 오후 1 42 12" src="https://user-images.githubusercontent.com/29944530/93425058-3863e180-f8f4-11ea-824f-66db0a7a1d1e.png">

<img width="1525" alt="스크린샷 2020-09-17 오전 12 13 50" src="https://user-images.githubusercontent.com/29944530/93425076-3c8fff00-f8f4-11ea-9f86-01d4a6f9563f.png">

<img width="1721" alt="스크린샷 2020-09-17 오후 12 41 01" src="https://user-images.githubusercontent.com/29944530/93425072-3b5ed200-f8f4-11ea-9c23-68697e696437.png">
<img width="1221" alt="스크린샷 2020-09-17 오전 12 18 42" src="https://user-images.githubusercontent.com/29944530/93425074-3bf76880-f8f4-11ea-8467-23e4525be10e.png">


# 기능
1. order 하기
![order 캡쳐](https://user-images.githubusercontent.com/60597630/93294322-2109f300-f825-11ea-983a-75d9d47b34eb.JPG)
![order 캡쳐2](https://user-images.githubusercontent.com/60597630/93294330-223b2000-f825-11ea-94f4-fce9b5ac5af2.JPG)

2. shipped 하기
<img width="1359" alt="deliverystart" src="https://user-images.githubusercontent.com/29944530/93426212-8e398900-f8f6-11ea-97d8-80dbf50fffa5.png">

3. reviewRequested, reviewWrite
<img width="1177" alt="testflow" src="https://user-images.githubusercontent.com/29944530/93425047-34d05a80-f8f4-11ea-898d-3b57b37c3156.png">
<img width="1359" alt="reviewWrite" src="https://user-images.githubusercontent.com/29944530/93427496-de194f80-f8f8-11ea-9c4e-7aaf6822109d.png">

4.Feingclient
<img width="467" alt="foreign" src="https://user-images.githubusercontent.com/29944530/93427486-da85c880-f8f8-11ea-9c19-f7f631d79b01.png">

5. CI/CD 구현
- buildspec, codebuild 적용
<img width="2408" alt="Codebuild" src="https://user-images.githubusercontent.com/29944530/93427744-4a944e80-f8f9-11ea-958f-5389b43e53af.png">

6. autoscale 적용
<img width="467" alt="auto" src="https://user-images.githubusercontent.com/29944530/93428013-bbd40180-f8f9-11ea-9ac1-99373100f9ab.png">
- pod 1개
![autoscale-before](https://user-images.githubusercontent.com/60597630/93286459-45a89f80-f812-11ea-92ff-c260ea110bbe.JPG)
- 부하 발생시 pod 2개로 증가
![autoscale-after](https://user-images.githubusercontent.com/60597630/93286455-45100900-f812-11ea-921f-8080af36f499.JPG)

7. poliglot
-
<img width="761" alt="poliglot" src="https://user-images.githubusercontent.com/29944530/93425066-3a2da500-f8f4-11ea-8cf0-79b5379300eb.png">
