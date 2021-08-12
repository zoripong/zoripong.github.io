# 웹 푸시와 FCM 구현하기

[express.js]를 이용하여 웹 서비스를 만들던 중 채팅 기능과 메시지를 보낼 때 수신자에게 푸시 알림 구현이 필요로 했다.
이번 글에서는 FCM과 웹 푸시를 이용하여 채팅 기능을 구현하는 것을 소개하려고 한다.


## web push 구현하기

### 의존성 설치

```bash
npm install dotenv body-parser express web-push -S
```
- dotenv: Loads environmental variables from a .env file to process.env.
- express: Web application framework for Node.
- body-parser: Middleware for parsing incoming request bodies.
- web-push: Web Push library for Node.js.



### 서비스 워커?

## fcm 연결하기




## 참고
- https://pusher.com/tutorials/push-notifications-node-service-workers


[express.js]: https://expressjs.com/
#nodejs #expressjs #pwa #service_worker #fcm #firebase