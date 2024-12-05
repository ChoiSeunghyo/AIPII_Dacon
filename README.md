# AIPII_Dacon
## 이미지 색상화 및 손실 부분 복원 AI

-----
+ <https://dacon.io/competitions/official/236420/overview/description>
-----
  
### 1. 기본 Baseline


1-1. 전처리: 이미지를 256x256으로 크기 조정, 텐서 변환, 정규화 처리


1-2. 구현 방식: U-Net 구조, PatchGAN

+ Generator: U-Net 구조를 활용하여 복원 이미지 생성
+ Discriminator: PatchGAN을 사용해 생성된 이미지의 진짜/가짜 여부를 평가

