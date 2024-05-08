---
title: transition 속성
author: explorersm11
date: 2023-12-28 08:59:00 +0900
categories: [CSS, Attribute]
tags: [css, attribute, til, transition]
render_with_liquid: false
---

HTML요소를 다양하게 변형  

## transition-property
---
- <span style="background-color: #fff5b1">전환 효과를 줄 CSS 속성명 지정</span>
- all을 입력하면 전체 속성을 지정
- 속성값 : 속성명
```css
transition-property: transform opercity;
```
    
## transition-duration
---
- <span style="background-color: #fff5b1">전환 효과가 발생할 때 지속시간 지정</span>
- 속성값 : 지속시간(초 단위)
```css
transition-duration: 0.5s /* 0.5초 */
```

## transition-delay
---
- <span style="background-color: #fff5b1">전환 효과가 발생할 때 지연시간 지정</span>
- 지연시간 이후 전환효과가 나타남
- 속성값 : 지연시간(초 단위)
  
## transition-timing-function
---
- <span style="background-color: #fff5b1">전환 효과의 가속도 지정</span>
- 속성값 : 가속도
  - linear : 등속
  - ease : 가속
  - ease-in : 모션 시작 시 가속
  - ease-out : 모션 종료 시 가속
  - ease-in-out : 묘선 시작, 종료 시 모두 가속
  - cubic-bezier : 사용자 지정 가속
- <https://cubic-bezier.com>

## transition
---
- <span style="background-color: #fff5b1">모든 전환 효과의 속성값을 한꺼번에 축약해서 사용</span>
- 속성값 : 속성명, 지속시간, 가속도, 지연시간 순