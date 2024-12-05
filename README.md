# AIPII_Dacon
## 이미지 색상화 및 손실 부분 복원 AI

-----
+ <https://dacon.io/competitions/official/236420/overview/description>
-----

![손상된 이미지](https://github.com/ChoiSeunghyo/AIPII_Dacon/blob/main/TEST_000.png)
-----
  
### 1. 기본 Baseline


1-1. 전처리: 이미지를 256x256으로 크기 조정, 텐서 변환, 정규화 처리


1-2. 구현 방식: U-Net 구조, PatchGAN

+ Generator(U-Net): 다운샘플링과 업샘플링 블록 사용, Skip connection, Tanh를 사용해 -1~1로 정규화된 이미지 생성
+ Discriminator(PatchGAN): 복원된 이미지의 국소적인 패치를 분석, 현실적인 이미지인지 평가, 손상된 이미지와 복원된 이미지를 결합하여 입력으로 사용


1-3. 결과

+평가 산식: SSIM, 색상 Histogram 유사도
+ S: 전체 SSIM 평균
+ M: 손실 영역 SSIM 평균
+ C: 색상 유사도 평균
+ Score = (0.2 x S) + (0.4 x M) + (0.4 x C)

![결과1](https://github.com/ChoiSeunghyo/AIPII_Dacon/blob/main/test_1.png)  

-----

### 2. 코드공유(public 0.47243) U-net+PatchGAN Discriminator (epoch28))


2-1. 전처리: 이미지 값을 [0,1] 범위로 정규화, (H, W, C)에서(C, H, W) 형식으로 변환


2-2. 구현 방식: U-Net 구조, PatchGAN

+ Generator(U-Net): 다운샘플링과 업샘플링 블록 사용, Skip connection
+ Discriminator(PatchGAN): 복원된 이미지의 국소적인 패치를 분석, 현실적인 이미지인지 평가, 손상된 이미지와 복원된 이미지를 결합하여 입력으로 사용
+ 학습이 끝난 후, 테스트 데이터를 복원한 이미지와 .zip 파일 생성


2-3. 결과

![결과2](https://github.com/ChoiSeunghyo/AIPII_Dacon/blob/main/test_2.png)


-----

### 3. 2코드에서 수정


3-1. 추가 코드

+ 모델이 판별기의 "진짜" 판단에 과도하게 의존하지 않도록 학습을 안정화
+ 생성기의 성능 개선

![코드추가](https://github.com/ChoiSeunghyo/AIPII_Dacon/blob/main/%2Bcode.png)


3-2. 결과

+ 2 와 비교함

![결과3](https://github.com/ChoiSeunghyo/AIPII_Dacon/blob/main/test_3.png)
