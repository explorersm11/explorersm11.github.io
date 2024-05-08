---
title: "java.io.UncheckedIOException: Cannot delete"
author: explorersm11
date: 2024-02-13 19:24:00 +0900
categories: [SpringBoot, SpringBoot Troubleshooting]
tags: [springboot, spring, aws, troubleshooting]
render_with_liquid: false
---  
## <span style="background-color: #fff5b1">🧨오류 내용</span>
```
java.io.UncheckedIOException: Cannot delete C:\Users\smhrd\AppData\Local\Temp\tomcat.8089.1070292282324288404\work\Tomcat\localhost\medit\upload_09e1bcb3_1796_4afb_b0a8_86783c1dc4d2_00000001.tmp
...
Caused by: java.io.IOException: Cannot delete C:\Users\smhrd\AppData\Local\Temp\tomcat.8089.1070292282324288404\work\Tomcat\localhost\medit\upload_09e1bcb3_1796_4afb_b0a8_86783c1dc4d2_00000001.tmp
...
java.io.UncheckedIOException: Cannot delete C:\Users\smhrd\AppData\Local\Temp\tomcat.8089.1070292282324288404\work\Tomcat\localhost\medit\upload_09e1bcb3_1796_4afb_b0a8_86783c1dc4d2_00000001.tmp
...
2024-02-13 18:46:15.802 ERROR 4908 --- [nio-8089-exec-1] org.apache.tomcat.util.net.NioEndpoint   : Error running socket processor
```

<br>

## <span style="background-color: #fff5b1">🔧해결 방법</span>

- 스프링부트 버전 문제로 발생
- 버전을 2.7.6으로 변경하였음
  ```xml
  <parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.7.6</version>
		<relativePath/>
	</parent>
  ```
