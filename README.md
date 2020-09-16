# D조
- 배한진 수석,유희명 수석, 조웅철 선임, 송준호 수석, 이상돈 수석 
# 주제 : 꽃 배달 

# 기능적 요구사항
- 고객이 꽃배달 메뉴 선택하여 주문한다
- 주문이 되면 결제 시스템의 결제 기능이 호출된다
- 결제가 완료되면 주문 내역이 꽃가게 주인에게 전달된다
- 꽃가게 주인이 주문을 확인하여 꽃을 만들어 배송을 시작한다
- 고객이 주문을 취소할 수 있다
- 주문이 취소되면 배송이 취소된다
- 고객이 주문상태를 조회한다
- 주문상태가 바뀔 때 SMS로 알림을 보낸다

# 이벤트스토밍
<img width="1920" alt="스크린샷 2020-09-16 오전 8 56 38" src="https://user-images.githubusercontent.com/29944530/93278534-ee013880-f7ff-11ea-8787-86510a5ddacc.png">

# 시연
1. order 하기
- http http://a0b3b3575651b4e85922eb5bcb5840cf-455819388.ap-northeast-2.elb.amazonaws.com:8080/orders flowerName=Rose qty=7 address=seoul customerName=lee phoneNumber=01012341234

2. delivery 확인
- http http://a0b3b3575651b4e85922eb5bcb5840cf-455819388.ap-northeast-2.elb.amazonaws.com:8080/deliveries

3. shipped 하기
- http PATCH http://a0b3b3575651b4e85922eb5bcb5840cf-455819388.ap-northeast-2.elb.amazonaws.com:8080/deliveries/2 status="DeliveryStart"

4. mypage 실행
- http http://a0b3b3575651b4e85922eb5bcb5840cf-455819388.ap-northeast-2.elb.amazonaws.com:8080/mypages

5. cancel하기
- http PATCH http://a0b3b3575651b4e85922eb5bcb5840cf-455819388.ap-northeast-2.elb.amazonaws.com:8080/orders/1 status="OrderCancelled"

6. CI/CD 구현
- buildspec, codebuild 적용
![buildspec](https://user-images.githubusercontent.com/60597630/93287560-c9638b80-f814-11ea-9c9b-f5ac701809e6.JPG)
![cicd](https://user-images.githubusercontent.com/60597630/93287562-ca94b880-f814-11ea-8d12-81127393512e.JPG)

7. circuit breaker 적용
- siege -c50 -t30S  -v --content-type "application/json" 'http://order:8080/orders POST {"flowerName":"AAAA","qty":5}' 으로 테스트
![circuit breaker](https://user-images.githubusercontent.com/60597630/93287119-ac7a8880-f813-11ea-8df0-25ea88183f27.JPG)

8. autoscale 적용
- pod 1개
![autoscale-before](https://user-images.githubusercontent.com/60597630/93286459-45a89f80-f812-11ea-92ff-c260ea110bbe.JPG)
- 부하 발생시 pod 2개로 증가
![autoscale-after](https://user-images.githubusercontent.com/60597630/93286455-45100900-f812-11ea-921f-8080af36f499.JPG)

9. Jaeger 모니터링 적용 (http://a754bd45eff4d4b72af3ccbf2987bf6c-1373967310.ap-northeast-2.elb.amazonaws.com:16686)
![jaeger](https://user-images.githubusercontent.com/60597630/93286820-09297380-f813-11ea-8938-782a1ae0981c.JPG)

10. Kiali 모니터링 적용 (http://ae72f8a7283174456888fb7236a765e9-1825562489.ap-northeast-2.elb.amazonaws.com:20001)
![kiari](https://user-images.githubusercontent.com/60597630/93286819-07f84680-f813-11ea-832b-002d18e7c4bb.JPG)
