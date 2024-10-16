<div align="center">

## 🚗 ADAS (Advanced Driver Assistance Systems) 프로젝트

![AutoAware Logo](https://github.com/user-attachments/assets/29708dde-6bec-4741-8185-6e4d7bf6c01c)

</div>

고급 운전자 보조 시스템(ADAS)을 구현한 이 프로젝트는 영상 및 이미지에서 차선과 객체를 감지하여 운전자에게 실시간으로 경고를 제공합니다. 🛣️👀

## ✨ 주요 기능
1. 🛣️ **차선 감지**: 정확한 알고리즘을 사용하여 도로의 차선을 식별합니다.
2. 🚙👨‍🦯🏍️ **객체 감지**: YOLO를 사용하여 차량, 보행자, 오토바이 등 다양한 도로 위의 객체를 감지합니다.
3. ⚠️ **위험 상황 경고**: 잠재적인 위험을 식별하고 운전자에게 시각적 경고를 제공합니다.

## 🔍 사용된 기술
### YOLO (You Only Look Once)
이 프로젝트는 객체 감지를 위해 YOLO v8을 사용합니다. YOLO는 실시간 객체 감지 시스템으로, 높은 정확도와 빠른 처리 속도를 자랑합니다.
- **빠른 처리 속도**: 실시간 비디오 스트림에서도 효과적으로 작동합니다.
- **다양한 객체 감지**: 차량, 보행자, 오토바이 등 여러 종류의 객체를 동시에 감지할 수 있습니다.
- **높은 정확도**: 최신 버전의 YOLO는 높은 mAP (mean Average Precision)를 제공합니다.

YOLO 모델은 `models/adas_car_detection.pt` 파일에 저장되어 있으며, `ultralytics` 라이브러리를 통해 로드됩니다.

### UNet++
차선 검출을 위해 UNet++ 아키텍처를 사용합니다. 이 모델은 `pytorch-nested-unet` 디렉토리에서 훈련되고 관리됩니다.

## 📁 파일 설명
### 1. adas_model.ipynb 🔧
ADAS 시스템의 핵심 구성 요소를 개발하는 전체 워크플로우를 포함합니다.
- 📥 데이터셋 다운로드 및 전처리
- 🏋️ YOLO 모델 훈련 및 평가
- 🛠️ NestedUNet을 이용한 차선 검출 모델 개발
- 📊 모델 성능 평가 및 분석
  
### 2. adas_image.ipynb 🖼️
정지 이미지를 처리하여 ADAS 기능을 시연합니다.
- 📊 이미지에서 차선 감지
- 🔍 YOLO를 사용한 객체 감지 및 분류
- 🚨 위험 상황 식별 및 경고 표시
- 💾 처리된 이미지 저장

### 3. adas_video.ipynb 🎥
비디오 스트림을 실시간으로 처리하여 ADAS 기능을 구현합니다.
- 🎞️ 비디오 스트림에서 연속적인 차선 감지
- 🏃‍♂️ YOLO를 사용한 실시간 객체 감지 및 분류
- 🚦 동적 위험 상황 식별 및 경고 표시
- 📼 처리된 비디오 저장

## 🖼️ 결과 확인
### 이미지 처리 결과
| 이미지 1 | 이미지 2 |
|:--------:|:--------:|
| ![Image 1](https://github.com/user-attachments/assets/f85b6cef-d46e-49c2-8c5f-b4fb6b2c4dfb) | ![Image 2](https://github.com/user-attachments/assets/e8625275-c40d-4ac9-9273-ee964b4fa211) |
| 이미지 3 | 이미지 4 |
| ![Image 3](https://github.com/user-attachments/assets/8629dbca-de6d-4282-8153-c447c857b226) | ![Image 4](https://github.com/user-attachments/assets/e1d07141-b96f-4df0-a273-94e6fe5287c5) |
### 비디오 처리 결과
| 비디오 1 | 비디오 2 |
|:--------:|:--------:|
| [![Video 1](https://img.youtube.com/vi/8sZi3NrCKGw/0.jpg)](https://www.youtube.com/watch?v=8sZi3NrCKGw) | [![Video 2](https://img.youtube.com/vi/tgSD75RHLqw/0.jpg)](https://www.youtube.com/watch?v=tgSD75RHLqw) |

## 🛠️ 설치 및 실행
1. **필요한 라이브러리 설치:**
   ```bash
   pip install numpy opencv-python matplotlib pytorch ultralytics 
   ```

2. **프로젝트 구조:**
   ```
   📂 project_root/
   ┣ 📂 models/
   ┃ ┣ 📄 adas_car_detection.pt  # YOLO 모델 파일
   ┃ ┣ 📄 adas_lane_segmentation.pth
   ┃ ┗ 📄 config.yml
   ┣ 📂 dataset/
   ┃ ┣ 📂 images/
   ┃ ┣ 📄 video.mp4
   ┃ ┗ 📂 processed_images/
   ┣ 📂 pytorch-nested-unet/
   ┃ ┗ [차선 검출 모델 관련 파일들]
   ┣ 📓 adas_image.ipynb
   ┣ 📓 adas_video.ipynb
   ┗ 📓 adas_model.ipynb
   ```
3. **모델 훈련:**
   - `Project2ADAS.ipynb`를 실행하여 YOLO 모델과 차선 검출 모델을 처음부터 훈련시킬 수 있습니다.
   - 이 과정은 상당한 시간과 컴퓨팅 리소스가 필요할 수 있습니다.

## 📝 참고사항
- YOLO 모델 훈련에는 CUDA 지원 GPU를 사용하는 것이 좋습니다.
- 차선 검출 모델 (UNet++)은 `pytorch-nested-unet` 디렉토리에서 관리됩니다.
