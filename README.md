# 탐정: 렌즈 속 비밀

태그: SSAFY

# 탐정: 렌즈 속 비밀

**💻 모바일(안드로이드) 어플리케이션**

**📅 2022.08 - 2022.010**

**🏢 삼성 청년 SW 아카데미 특화 프로젝트**

## 담당 직무

---

AI(Yolo V5), Frontend(React, React Native - Camera), Server

## 담당 업무

---

- 데이터 전처리 [AI]
- 데이터 학습 [AI]
- 이미지 디텍팅 [AI]
- Android Application 배포용 사이트 (탬플릿 사용) [프론트엔드]
- Android Application 빌드 (React Native)
- Server 세팅(Ai, Nginx, DB, SSL) [DevOps]

## 참여 인원

---

- Back-End 1명
- Front-End 2명
- 디자인 1명
- 스토리 1명
- AI 1명

## 성과

---

2022.10 SSAFY 특화 프로젝트 우수상 (1등)

## 링크

---

- Github 바로가기
- 개발로그 [Notion 바로가기](https://www.notion.so/488cbfb9c3d04692bf656a43dda19b3f?pvs=21)

## 개발환경

---

- IDE
    - PyCharm
    - IntelliJ
    - VSC
    - MobaXterm
    - Blender
- Lib
    - Spring Boot
    - React
    - React Native
    - Yolo V5
    - PyTorch
    - mysql
- language
    - JAVA
    - Python
    - Java Script

## AI [Image Detecting]

---

> Yolo V5 설정
> 
- 다운로드
    - 원하는 위치에 아래 명령어로 소스 다운로드
        
        ```jsx
        git clone [https://github.com/ultralytics/yolov5.git](https://github.com/ultralytics/yolov5.git)
        ```
        

- 라이브러리 설치
    - 아래 명령어로 라이브러리 설치
        
        ```jsx
        pip install -r requirements.txt
        ```
        

- 데이터 위치 설정 (train.py)
    - 기존 데이터 경로 및 정보파일 이름 수정
        
        ```jsx
        parser.add_argument('--data', type=str, default=ROOT / 'data/sample.yaml', help='dataset.yaml path')
        ```
        
    
    - worker 수 조정
        
        ```jsx
        parser.add_argument('--workers', type=int, default=0, help='max dataloader workers (per RANK in DDP mode)')
        ```
        

- 데이터 정보 설정 (.yaml)
    - yolo폴더 내 data로 이동 후 yaml 파일 생성
    - 아래 내용 추가 및 기존 데이터 값 추가
        
        ```jsx
        path: ../datasets/sampleData# dataset root dir
        train: train/images# train images (relative to 'path') 128 images
        val: train/images# val images (relative to 'path') 128 images
        test: # test images (optional)
        nc: 7
        names: ['fish', 'jellyfish', 'penguin', 'puffin', 'shark', 'starfish', 'stingray']
        ```
        
        - path : 이미지, 라벨 폴더가 존재하는 루트 폴더
        - train : 학습시킬 이미지가 있는 폴더
        - nc : 이미지에 있는 클래스 갯수
        - names : 이미지에 있는 클래스 이름 (앞에서부터 0번)
        

> Train
> 
- 데이터 전처리 - 라벨 파일 양식 : 클래스 명, 네 모서리 좌표값(4개)
- [train.py](http://train.py) 파일 실행
- 결과
    
    
    - R_curve
        
        ![R_curve](https://github.com/sonjuhy/Detective/assets/2987059/ff5f7431-e2f1-45e3-8e28-25a3b341b382)
        
    
    - P_curve
        
        ![P_curve](https://github.com/sonjuhy/Detective/assets/2987059/16fb5169-d6f9-42ff-adcd-e175209a1100)
        
    - results
        
        ![results](https://github.com/sonjuhy/Detective/assets/2987059/68ae8436-8dd8-43d7-b66f-42755bcbbae1)
        
    - batch
        
        ![Untitled](https://github.com/sonjuhy/Detective/assets/2987059/7a1e2c6d-d912-430b-b32d-5dc5528c1c40)
        

> Detect
> 
- [detect.py](http://detect.py) 실행
    
    ![fish](https://github.com/sonjuhy/Detective/assets/2987059/c9ffdcb5-a8c8-48b1-a0f0-c53f0d74559d)
    

## 구조도

---

![Untitled 1](https://github.com/sonjuhy/Detective/assets/2987059/8ca6e030-9019-4555-a20c-b03a2de08b96)

## 서비스 화면

---

### 사진 선택

> 사진 선택(혹은 촬영)
> 
- 사진을 선택(혹은 촬영) 후 서버로 전송하여 분석 결과를 요청합니다.
    
    ![Untitled 2](https://github.com/sonjuhy/Detective/assets/2987059/2fb9f253-4102-46ba-ae0c-67769c4cb5e8)
    

### 사진 분석 결과 (정답)

> 사진 분석 결과 (정답)
> 
- 전송한 사진의 분석 결과가 해당하는 단서가 있을 경우 스크립트가 진행됩니다.
    
    ![Untitled 3](https://github.com/sonjuhy/Detective/assets/2987059/7430ce42-e979-4a3e-aeee-669ae0b06651)
    

### 사진 분석 결과 (오답)

> 사진 분석 결과 (오답)
> 
- 전송한 사진의 분석 결과가 해당하는 단서가 없을 경우 아래 사진처럼 진행됩니다.
    
    ![Untitled 4](https://github.com/sonjuhy/Detective/assets/2987059/3d537980-4348-44a4-8557-8c21f84b38f7)
    

### 사진 분석 결과 (중복)

> 사진 분석 결과 (중복)
> 
- 전송한 사진의 분석 결과가 이미 조사한 단서일 경우 아래 사진처럼 진행됩니다.
    
    ![Untitled 5](https://github.com/sonjuhy/Detective/assets/2987059/3a5c0528-1163-4f6c-a5bb-5d909785b6eb)
