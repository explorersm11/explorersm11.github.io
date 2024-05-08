---
title: transform 속성
author: explorersm11
date: 2023-12-27 17:22:00 +0900
categories: [CSS, Attribute]
tags: [css, attribute, til, transform]
render_with_liquid: false
---

요소의 속성값이 변경될 때, 시간을 지정하여 일정 시간동안 부드러운 모션처리  

## transform(2D)
---
- **scale** : 선택 요소 크기를 확대, 축소    
  * 1을 기준으로 적으면 축소, 크면 확대
    
- **skew** : 선택 요소를 x축 또는 y축으로 비틀음
  * 단위 : deg[^degree]
  ```css
  transform: skewX(45deg);
  ```

- **translate** : 선택 요소를 x축 또는 y축으로 이동
  * x축 : 음수(좌), 양수(우)
  * y축 : 음수(상), 양수(하)
  ```css
  transform: translateY(20px)
  ```

- **rotate** : 선택 요소를 원하는 가도로 회전


## transform(3D)
---
- **rotate** : 선택 요소를 x축 또는 y축으로 입체감있게 회전
  ```css
  transform: rotateX(55deg)
  ```
- **translateZ** : 선택 요소를 z축으로 입체감있게 이동

## perspective
---
- 3D효과가 적용된 요소가 입체감있게 보이도록 <span style="background-color: #fff5b1">부모요소</span>에 perspective 속성을 적용하여 원근감 부여
- 속성값 : px
- 작을수록 3D요소에 왜곡이 심하고, 클수록 완만해짐
- <span style="background-color: #fff5b1">반드시 부모요소에 perspective 속성을 적용해줘야 왜곡현상이 강제로 적용됨</span>

## transform-origin
---
- 요소의 변형이 일어나는 중심축을 가로축, 세로축 기준으로 변경
  + transform-origin: center top; (가로축, 세로축)

<br>

> 이동: px, 각도: deg
{: .prompt-tip }

<br>
<br>

[^degree]: degree(각도)