---
title: animation 속성
author: explorersm11
date: 2023-12-28 10:59:00 +0900
categories: [CSS, Attribute]
tags: [css, attribute, til, animation]
render_with_liquid: false
---

사용자가 동작을 하지 않아도 미리 지정한 조건에 맞게 자동으로 반복하는 애니메이션 효과 부여

## @keyframes
---
- <span style="background-color: #fff5b1">애니메이션 시작과 끝을 등록하여 사용자 모션 등록</span>
- 0% (시작) <----> 100% (끝)
- 중간 지점은 여러개 추가 가능
- 속성값 : 애니메이션 세트 지정 (animation-name에 사용될 이름)

## animation-name
---
- <span style="background-color: #fff5b1">키프레임으로 등록한 모션의 이름 호출</span>
- 속성값 : 키프레임 명

## animation-duration
---
- <span style="background-color: #fff5b1">키프레임 모션 한 세트를 얼마동안 동자갛게 할지 초단위 등록<span>
- 속성값 : 지속시간 (초 단위)

## animation-timing-function
---
- <span style="background-color: #fff5b1">키프레임 모션 실행 시 가속도 설정</span>
- 속성값 : 가속도 (transition 참고)

## animation-iteration-count
---
- <span style="background-color: #fff5b1">키프레임 모션 한 세트가 몇 번 동작하는지 횟수 설정</span>
- 속성값 : 횟수
- 무한반복 : infinite

## animation-delay
---
- <span style="background-color: #fff5b1">키프레임 모션 실행 시 지연시간 지정</span>
- 속성값: 지연시간 (초 단위)

## animation-play-state
---
- <span style="background-color: #fff5b1">키프레임 모션 실행 시 동작 상태 지정</span>
- 속성값 : running, paused

## animation
---
- <span style="background-color: #fff5b1">축약 지정</span>
- 속성값 : 키프레임명, 지속시간, 가속도, 지연시간, 반복횟수
  