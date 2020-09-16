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

1. delivery 확인
- http http://a0b3b3575651b4e85922eb5bcb5840cf-455819388.ap-northeast-2.elb.amazonaws.com:8080/deliveries

1. orderdetail view 실행

1. shipped 하기
- http PATCH http://a0b3b3575651b4e85922eb5bcb5840cf-455819388.ap-northeast-2.elb.amazonaws.com:8080/deliveries/2 status="DeliveryStart"

1. mypage 실행
- http http://a0b3b3575651b4e85922eb5bcb5840cf-455819388.ap-northeast-2.elb.amazonaws.com:8080/mypages

1. cancel하기
- http PATCH http://a0b3b3575651b4e85922eb5bcb5840cf-455819388.ap-northeast-2.elb.amazonaws.com:8080/orders/1 status="OrderCancelled"

