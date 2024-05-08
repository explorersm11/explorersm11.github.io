---
title: "Failed to connect to service endpoint"
author: explorersm11
date: 2024-02-13 19:24:00 +0900
categories: [AWS, AWS Troubleshooting]
tags: [springboot, spring, aws, troubleshooting]
render_with_liquid: false
---  
## <span style="background-color: #fff5b1">🧨오류 내용</span>
```
com.amazonaws.SdkClientException: Failed to connect to service endpoint:
Caused by: java.net.SocketTimeoutException: connect timed out
```

<br>

## <span style="background-color: #fff5b1">🔧해결 방법</span>

- spring-cloud-starter-aws 의존성 주입시 로컬환경은 AWS환경이 아니기때문에 발생한다.
- 아래 구문을 SpringBootApplication에 적용하자.
  ```java
  @SpringBootApplication(
        exclude = {
                org.springframework.cloud.aws.autoconfigure.context.ContextInstanceDataAutoConfiguration.class,
                org.springframework.cloud.aws.autoconfigure.context.ContextStackAutoConfiguration.class,
                org.springframework.cloud.aws.autoconfigure.context.ContextRegionProviderAutoConfiguration.class
        }
   )
  ```

  
