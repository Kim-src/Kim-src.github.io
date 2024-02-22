---
title: 싱크홀(공동) 자동 분석 AI 모델 VisualCavity AI 개발 요약 내용(ver. 0.1.0)
date: 2024-03-09 21:00:00 +09:00
categories: [VisualCavity, AI Model]
tags: [Python, TensorFlow, AI, AI Model, Numpy]
---

<!-- 2099-01-01 글 작성 시작; 2099-01-01 페이지 호출 검토 필요 -->
## ✅ 싱크홀(공동) 자동 분석 AI 모델 VisualCavity AI 개발(ver. 0.1.0)

<br>

### 🔔 1. Introduction
### 📌 모델 소개
> - 모델명 : VisualCavity (ver. 0.1.0)
> - 모델분류 : 이미지 학습 CNN AI 모델
> - 상세내용 : 싱크홀(공동) 자동 분석 프로그램 제작을 위한 이미지 학습 AI 모델
> - 개발목적 : 3D-GPR 데이터 분석 난이도 하향
> - 주요자료 : GPR 공동 탐사 데이터 및 30만장의 이미지

<br>

### 🔔 2. Methodology
### 📌 개발 환경
> - Google Colab에서 Python 코드를 작성하였습니다.
> - 주로 사용된 Python 라이브러리는 TensorFlow, OpenCV 입니다.

### 📌 이미지 학습을 위한 코딩 순서
>   1. Python 내부 라이브러리 사용
>   2. 학습시킬 이미지 1장에 대한 JPG 및 XML 파일의 경로 설정
>   3. 이미지 전처리를 위한 함수 정의
>   4. 이미지 로드 및 전처리를 위한 함수 작성
>   5. XML 파일에서 이미지 정보 습득을 위한 함수 정의
>   6. XML 파일을 파싱 후 데이터 추출
>   7. CNN 모델 구성(CNN : 컨볼루션 신경망 : Convolution Neural Network)
>   8. 모델 컴파일(Compile : 사람이 작성한 코드를 컴퓨터에게 이해시키는 과정)
>   9. 모델에 입력할 이미지 및 레이블 데이터 세팅
>   10. 이미지 데이터를 모델에 맞게 형태 변환
>   11. 모델 훈련(epochs 활용)

<br>

### 🔔 3. Results : 전체 코드
### 📌 이미지 학습에 사용된 코드 및 간략한 설명
> - 이미지 학습에 사용된 전체적인 코드는 아래와 같습니다.
> - 각 코드마다 간략한 설명을 작성하였습니다.
> - 각 코드와 관련된 상세한 설명은 다음 글에 작성하였습니다.

<br>

```Python
# Python 내부 라이브러리 사용
import xml.etree.ElementTree as ET  # XML 파일을 파싱하기 위한 라이브러리를 사용하였습니다.
import cv2  # 이미지 처리 및 컴퓨터 비전 작업을 위한 OpenCV 라이브러리를 사용하였습니다.
import numpy as np  # 이미지 배열을 위한 라이브러리를 사용하였습니다.
import tensorflow as tf  # 딥러닝 모델 구축을 위한 TensorFlow 라이브러리를 사용하였습니다.
from tensorflow.keras import layers, models  # 모델의 레이어를 적용하기 위해 TensorFlow의 Keras API를 사용하였습니다.
from tensorflow.keras.preprocessing import image  # 이미지 로드 및 전처리를 위한 함수를 사용하였습니다.
from tensorflow.keras.preprocessing.image import img_to_array  # 이미지를 넘파이 배열로 변환하는 함수를 사용하였습니다.

# 학습시킬 이미지 1장에 대한 JPG 및 XML 파일의 경로 설정
image_path = "/content/drive/MyDrive/MyPJT/Cavity_PJT/cavity_sample_img.jpg" # JPG 파일 경로입니다.
xml_path = "/content/drive/MyDrive/MyPJT/Cavity_PJT/cavity_sample_xml.xml" # XML 파일 경로입니다.

# 이미지 전처리를 위한 함수 정의
def preprocess_image(image_path, target_size=(256, 256)):
    img = image.load_img(image_path, target_size=target_size)  # 이미지를 로드하고 target_size로 크기를 조정하였습니다.
    img_array = img_to_array(img)  # 이미지 배열을 Numpy에 맞게 변환하였습니다.
    img_array = np.expand_dims(img_array, axis=0)  # 이미지 배열 관련 배치 차원을 추가하였습니다.
    img_array /= 255.0  # 이미지를 0과 1 사이의 값으로 정규화합니다.
    return img_array  # 전처리된 이미지 배열을 반환합니다.

# 이미지 로드 및 전처리를 위한 함수 작성
img_array = preprocess_image(image_path)

# XML 파일에서 이미지 정보 습득을 위한 함수 정의
def parse_annotation(xml_path):
    tree = ET.parse(xml_path)  # XML 파일을 파싱합니다.
    root = tree.getroot()  # 파싱된 XML의 루트 엘리먼트를 가져옵니다.

    filename = root.find('filename').text  # 이미지 파일 이름을 추출합니다.
    object_name = root.find('.//object/name').text  # 객체의 이름을 추출합니다.

    # 바운딩 박스 좌표 추출(ROI : Region of Interst)
    xmin = float(root.find('.//bndbox/xmin').text)
    ymin = float(root.find('.//bndbox/ymin').text)
    xmax = float(root.find('.//bndbox/xmax').text)
    ymax = float(root.find('.//bndbox/ymax').text)

    return filename, object_name, xmin, ymin, xmax, ymax  # 추출한 정보를 반환합니다.

# XML 파일을 파싱 후 데이터 추출
filename, object_name, xmin, ymin, xmax, ymax = parse_annotation(xml_path)

# CNN 모델 구성(CNN : 컨볼루션 신경망 : Convolution Neural Network)
model = models.Sequential()
model.add(layers.Conv2D(32, (3, 3), activation='relu', input_shape=(256, 256, 3)))
model.add(layers.MaxPooling2D((2, 2)))
model.add(layers.Conv2D(64, (3, 3), activation='relu'))
model.add(layers.MaxPooling2D((2, 2)))
model.add(layers.Conv2D(64, (3, 3), activation='relu'))
model.add(layers.Flatten())  # 3D 특성 맵을 1D 텐서로 평탄화합니다.
model.add(layers.Dense(64, activation='relu'))
model.add(layers.Dense(1, activation='sigmoid'))  # 이진 분류를 위한 출력 레이어를 추가합니다.

# 모델 컴파일(Compile : 사람이 작성한 코드를 컴퓨터에게 이해시키는 과정)
model.compile(optimizer='adam',
              loss='binary_crossentropy',  # 이진 분류 손실 함수를 사용합니다.
              metrics=['accuracy'])  # 정확도를 평가 지표로 사용합니다.

# 모델에 입력할 이미지 및 레이블 데이터 세팅
X_train = np.array([img_array])  # 이미지 배열을 넘파이 배열로 변환합니다.
y_train = np.array([1])  # 이진 분류의 경우, 레이블을 넘파이 배열로 변환합니다.

# 이미지 데이터를 모델에 맞게 형태 변환
X_train = np.squeeze(X_train, axis=0)

# 모델 훈련(Epochs 활용)
model.fit(X_train, y_train, epochs=5, batch_size=1)
```

<br>

### 🔔 3. Results : 코드 상세 설명
### 📌 

<br>

### 🔔 4. Conclustions
### 📌 AI 모델 생성 결과
epoch가 ~


<br>

### 🎁 5. Appendix
### 🚀 개발 현황 : VisualCavity AI (현재 ver. 0.1.0)
> - v0.1.0 : 이미지 1장 학습 완료 (2024-01-09)
> - v0.1.3 : 이미지 1장 학습에 대한 검토 완료
> - v0.1.7 : 학습한 이미지 1장을 가지고 다른 이미지 대조 완료
> - v0.2.0 : 이미지 100장 학습 완료
> - v0.2.3 : 이미지 100장 학습에 대한 검토 완료
> - v0.2.7 : 학습한 이미지 100장을 가지고 다른 이미지를 대조한 뒤 버전 비교 완료
> - v0.3.0 : 이미지 1,000장 학습 완료
> - v0.3.3 : 이미지 1,000장 학습에 대한 검토 완료
> - v0.3.7 : 학습한 이미지 1,000장을 가지고 다른 이미지를 대조한 뒤 버전 비교 완료
> - v0.4.0 : 이미지 10,000장 학습에 대한 검토 완료
> - v0.4.3 : 이미지 10,000장 학습에 대한 검토 완료
> - v0.4.7 : 학습한 이미지 10,000장을 가지고 다른 이미지를 대조한 뒤 버전 비교 완료
> - v0.5.0 : 이미지 100,000장 학습에 대한 검토 완료
> - v0.5.3 : 이미지 100,000장 학습에 대한 검토 완료
> - v0.5.7 : 학습한 이미지 100,000장을 가지고 다른 이미지를 대조한 뒤 버전 비교 완료
> - v0.6.0 : 이미지 300,000장(보유중인 이미지 개수) 학습에 대한 검토 완료
> - v0.6.3 : 이미지 300,000장 학습에 대한 검토 완료
> - v0.6.7 : 학습한 이미지 300,000장을 가지고 다른 이미지를 대조한 뒤 버전 비교 완료
> - v0.7.0 : 이미지가 학습된 AI 모델을 이용하여 50m 길이의 탐사 데이터 분석
> - v0.7.1 : 탐사 데이터 분석 성공률 10% 달성  
>   수많은 에러 발생 가능성 증가 예상
> - v1.0.0 : AI를 이용한 싱크홀 분석 모델 생성  
>   AI 모델을 이용한 싱크홀 분석 프로그램에 적용될 예정

<a href="https://kim-src.github.io/">Kim-src Blog</a>

<img src="https://github.com/Kim-src/Images/assets/150884526/9ba1ebbb-a79c-4e4c-a5f6-2149bb301cd8" class="img">

<br>

---

<br>
<br>
<br>
