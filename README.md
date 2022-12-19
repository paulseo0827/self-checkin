# Self Check-in using Amazon Rekognition

<b>Service Architecture</b>


![image](https://user-images.githubusercontent.com/56906461/208331253-d8b79a8b-624d-4a59-9962-36290981420c.png)



1) 숙소와 항공권 예매를 위해 사용자는 Mobile Device(Mobile phone, Tablet, Labtop 등)를 이용해서 예매 페이지에 접속. 웹페이지를 접속하기 위해 AWS의 DNS 서비스인 Amazon Route53 (https://aws.amazon.com/ko/route53/)을 통해 CDN 서비스인 Amazon CloudFront (https://aws.amazon.com/ko/cloudfront/)의 도메인 주소를 식별하여 예매 웹 사이트로 접속

2) Amazon CloudFront (https://aws.amazon.com/ko/cloudfront/)를 활용해서Amazon Elastic Kubernetes Service(EKS) (https://aws.amazon.com/ko/eks/) 에서 호스팅 하고 있는 예매 및 체크인 애플리케이션에 사용되는 정적/동적 웹사이트 컨텐츠들을 캐싱. 웹사이트의 요청에 빠른 응답을 제공 함을써 고객의 서비스 접근성 및 만족도를 향상

 3) AWS의 Container Orchestration 서비스인 Amazon Elastic Kubernetes Service(EKS) (https://aws.amazon.com/ko/eks/)를 통해 숙소와 항공권 예매를 하고, 자동 체크인을 위한 Front-end와 Back-end Logic을 처리할 수 있는 애플리케이션 컨테이너들을 호스팅해서 요청받은 API 기반의 Logic들을 원활하게 처리

4) AWS의 고성능 RDBMS 서비스인 Amazon Aurora (https://aws.amazon.com/ko/rds/aurora/)를 적용하여 애플리케이션의 데이터를 저장 하도록 구성 함으로써, 높은 성능과 가용성, 뛰어난 확장성과 보안이 적용 되도록 구성 (Amazon Aurora는 MySQL, PostgreSQL과 호환되는 완전 관리형 RDBMS 서비스)

5) 숙소와 항공권을 사전에 예매한 사용자는 AWS의 기계 학습을 통해 이미지 및 비디오 분석을 자동화 해주는 서비스인 Amazon Rekognition (https://aws.amazon.com/ko/rekognition/)을 사용하여 티켓 예매시 촬영한 이미지와 로그인시 촬영된 이미지를 AI/ML 기반으로 자동 분석하여 이미지가 매칭 시(얼굴 인식 성공 시) 성공적으로 체크인 및 티켓 발급
