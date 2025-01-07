---
title: "RAID(Redundant Array of Independent Disks)"
author: explorersm11
date: 2025-01-06 16:20:00 +0900
categories: [Linux, Study]
tags: [linux, til, cs]
render_with_liquid: false
published: true
---  

## ❓RAID란?
- 여러 개의 하드디스크가 있을 때, 동일한 데이터를 다른 위치에 중복해서 저장하는 방법
- 초기의 RAID : 저용량 하드디스크를 하나의 디스크로 확장하는데 사용
- 현재의 RAID : 백업, 안정적인 데이터 보존 및 유지, 속도 향상 → 결국엔 전체적인 성능 향상

### 💡스트라이핑(Striping)이란?
- 연속된 데이터를 여러 개의 디스크에 *라운드로빈 방식으로 기록하는 기술이다.<br>
        　　* 순환하면서 균등하게 분산

### 💡미러링(Mirroring)이란?
- 디스크에 에러 발생 시 데이터의 손실을 막기 위해 추가적으로 하나 이상의 장치에 중복 저장하는 기술이다.

<br>

## 💿 RAID 레벨
---

### **- RAID-0**

<div align = "left">
        <img src="https://github.com/user-attachments/assets/a8b897ae-aff6-4389-8232-bbe09ff55218" width="200" height="250">
</div>

- 스트라이핑 사용하여 빠른 입출력 속도 제공
- 데이터 중복이나 패리티 없이 디스크에 분산 기록
- 처리 속도가 빠르나, 하나라도 오류가 발생하면 데이터 복구 불가
- <span style = "color : red">**속도 추구**</span>

<br>

### **- RAID-1**

<div align = "left">
        <img src="https://github.com/user-attachments/assets/a2d18ff5-ae65-4632-8a58-3dc6bf4dbce4" width="200" height="250">
</div>

- 스트라이핑 사용하지 않고 미러릴 사용하여 두 개의 디스크에 데이터를 동일하게 기록
- 복구 능력 탁월
- 중복 저장으로 인한 디스크 낭비
- <span style = "color : red">안정성 추구</span>

<br>

### **- RAID-2**

<div align = "left">
        <img src="https://github.com/user-attachments/assets/df96b531-26da-4ac6-87b5-2358deaba69e" width="500" height="250">
</div>

- 스트라이핑 사용해서 디스크 구성
- 에러 감지 및 수정을 위해 ECC(Error Check & Correction) 정보 사용
- 최근엔 기본적으로 오류 정정 기능을 가지고 있어서 거의 쓰지 않는다

<br>

### **- RAID-3**

<div align = "left">
        <img src="https://github.com/user-attachments/assets/74ebd909-c6b9-4a6d-827d-8ea6ba328b63" width="400" height="280">
</div>

- 스트라이핑 사용해서 디스크 구성
- 별도로 하나의 디스크에 패리티 정보 저장
- 입출력 작업이 동시에 모든 디스크에 대해 이루어지므로, 입출력을 겹치게 할 수 없다
- 대형 레코드가 많은 시스템에 이용
- 데이터 단위를 <span style = "color : green">바이트</span>로 나눈다
- RAID-3의 대두로 사용하지 않는 구성

<br>

### **- RAID-4**

<div align = "left">
        <img src="https://github.com/user-attachments/assets/4b912452-cdfa-467e-a8e5-84450f95080b" width="400" height="280">
</div>

- RAID-3보다 개선된 형태
- 블록 형태의 스트라이핑 기술을 사용하여 디스크 구성
- 데이터 단위를 <span style = "color : green">블록</span>으로 나눈다.
- 현재 거의 사용하지 않는 구성

> RAID-2, RAID-3, RAID-4는 모두 ECC를 사용한다. <br>
> 패리티를 특정 디스크에 저장하는 것은 병목 현상이 발생하기에 현재 거의 쓰지 않는다!

<br>

### **- RAID-5**

<div align = "left">
        <img src="https://github.com/user-attachments/assets/adeda9df-58c9-4da7-8145-ec20d9271fd5" width="400" height="280">
</div>

- 패리티 정보를 이용하여 하나의 디스크가 고장이 발생할 경우에도 사용 가능한 구성 방식
- <span style = "color : green">최소 3개</span>의 디스크로 구성
- 패리티 정보는 구성된 디스크에 분산하여 기록

<br>

### **- RAID-6**

<div align = "left">
        <img src="https://github.com/user-attachments/assets/b9341fb2-6133-4ebd-836b-feeb87e3c0d4" width="450" height="280">
</div>

- 전체적 구성은 RAID-5와 비슷하지만 디스크에 2차 패리티 구성을 포함함으로써 매우 높은 고장대비 능력을 발휘한다
- <span style = "color : green">최소 4개</span>의 디스크로 구성
- RAID-5에 비해 공간 효율성이나 처리속도는 떨어지나 데이터 신뢰도는 향상된다

<br>

### **- RAID-7**
- 하드웨어 컨트롤러에 내장되어 있는 **실시간 운영체제**를 사용하여 구성하는 방식
- 특정 업체에서만 이 방식을 사용한다

<br>

### **- RAID-0+1**

<div align = "left">
        <img src="https://github.com/user-attachments/assets/1186c667-2e2b-48a7-a9b2-745e647d4178" width="400" height="300">
</div>

- 디스크 2개를 RAID-0의 스트라이핑으로 구성하고, 이를 묶어 RAID-1 미러링으로 구성하는 방식

<br>

### **- RAID-10**

<div align = "left">
        <img src="https://github.com/user-attachments/assets/c736a447-3ea1-4a14-b68e-a61b07007c1b" width="400" height="300">
</div>

- RAID-0+1의 반대 개념
- 디스크 2개를 RAID-1 미러링으로 구성하고, RAID-0의 스트라이핑으로 구성하는 방식

<br>

### **- RAID-5+3**
- RAID-3 방식에 별도로 스트라이프를 구성하는 방식
- 보다 높은 성능을 제공하지만 구성 비용이 많이 든다