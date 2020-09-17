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

<img width="1177" alt="testflow" src="https://user-images.githubusercontent.com/29944530/93425047-34d05a80-f8f4-11ea-898d-3b57b37c3156.png">
<img width="1177" alt="스크린샷 2020-09-17 오후 1 42 12" src="https://user-images.githubusercontent.com/29944530/93425058-3863e180-f8f4-11ea-824f-66db0a7a1d1e.png">

<img width="1525" alt="스크린샷 2020-09-17 오전 12 13 50" src="https://user-images.githubusercontent.com/29944530/93425076-3c8fff00-f8f4-11ea-9f86-01d4a6f9563f.png">

<img width="761" alt="poliglot" src="https://user-images.githubusercontent.com/29944530/93425066-3a2da500-f8f4-11ea-8cf0-79b5379300eb.png">
<img width="1721" alt="SMS" src="https://user-images.githubusercontent.com/29944530/93425070-3ac63b80-f8f4-11ea-89be-63857b12d5fa.png">
<img width="1721" alt="스크린샷 2020-09-17 오후 12 41 01" src="https://user-images.githubusercontent.com/29944530/93425072-3b5ed200-f8f4-11ea-9c23-68697e696437.png">
<img width="1221" alt="스크린샷 2020-09-17 오전 12 18 42" src="https://user-images.githubusercontent.com/29944530/93425074-3bf76880-f8f4-11ea-8467-23e4525be10e.png">


# 기능
1. order 하기
- 

![order 캡쳐](https://user-images.githubusercontent.com/60597630/93294322-2109f300-f825-11ea-983a-75d9d47b34eb.JPG)
![order 캡쳐2](https://user-images.githubusercontent.com/60597630/93294330-223b2000-f825-11ea-94f4-fce9b5ac5af2.JPG)

2. delivery 확인
- http http://ab399056093b4495f9f7940d3e95c4f9-305412969.ap-northeast-2.elb.amazonaws.com:8080/deliveries

3. shipped 하기
- http PATCH http://ab399056093b4495f9f7940d3e95c4f9-305412969.ap-northeast-2.elb.amazonaws.com:8080/deliveries/2 status="DeliveryStart"

4. mypage 실행
- http http://ab399056093b4495f9f7940d3e95c4f9-305412969.ap-northeast-2.elb.amazonaws.com:8080/mypages

5. cancel하기
- http PATCH http://ab399056093b4495f9f7940d3e95c4f9-305412969.ap-northeast-2.elb.amazonaws.com:8080/orders/1 status="OrderCancelled"

6.Feingclient

![feignclient 캡처](https://user-images.githubusercontent.com/60597630/93294171-c7a1c400-f824-11ea-940b-2b9af777f7d1.JPG)

7. CI/CD, readiness/liveness 구현
- buildspec, codebuild 적용
![buildspec](https://user-images.githubusercontent.com/60597630/93287560-c9638b80-f814-11ea-9c9b-f5ac701809e6.JPG)
![cicd](https://user-images.githubusercontent.com/60597630/93287562-ca94b880-f814-11ea-8d12-81127393512e.JPG)

8. circuit breaker 적용
- siege -c50 -t30S  -v --content-type "application/json" 'http://order:8080/orders POST {"flowerName":"AAAA","qty":5}' 으로 테스트
![circuit breaker](https://user-images.githubusercontent.com/60597630/93287119-ac7a8880-f813-11ea-8df0-25ea88183f27.JPG)

9. autoscale 적용
- pod 1개
![autoscale-before](https://user-images.githubusercontent.com/60597630/93286459-45a89f80-f812-11ea-92ff-c260ea110bbe.JPG)
- 부하 발생시 pod 2개로 증가
![autoscale-after](https://user-images.githubusercontent.com/60597630/93286455-45100900-f812-11ea-921f-8080af36f499.JPG)

10. Jaeger 모니터링 적용 (http://a754bd45eff4d4b72af3ccbf2987bf6c-1373967310.ap-northeast-2.elb.amazonaws.com:16686)
![jaeger](https://user-images.githubusercontent.com/60597630/93286820-09297380-f813-11ea-8938-782a1ae0981c.JPG)

11. Kiali 모니터링 적용 (http://ae72f8a7283174456888fb7236a765e9-1825562489.ap-northeast-2.elb.amazonaws.com:20001)
![kiari](https://user-images.githubusercontent.com/60597630/93286819-07f84680-f813-11ea-832b-002d18e7c4bb.JPG)
