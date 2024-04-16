
# Safe-Eye: 비디오 감시 및 이상 행동 감지 시스템

Safe-Eye는 PySlowFast 모델과 Django 웹 프레임워크를 활용한 비디오 감시 및 이상 행동 감지 시스템입니다. 이 프로젝트는 CCTV 또는 보안 카메라에서 수집된 비디오 데이터를 실시간으로 분석하여 잠재적인 위험 상황을 탐지하고 대응할 수 있도록 설계되었습니다.

## 목차

I. [주요 기능](#주요-기능)
II. [기술 스택](#기술-스택)
III. [시스템 아키텍처](#시스템-아키텍처오늘-배포되는것-까지만-만들어서-업데이트-예정)
IV. [라이센스](#라이센스)
V. [기여](#기여)
VI. [팀 소개](#팀-소개)
VII. [와이어프레임](#와이어프레임)
VIII. [데이터베이스 모델링(ER Diagram)](#데이터베이스-모델링er-diagram)
IX. [프로젝트 폴더 구조](#프로젝트-폴더-구조)
X. [API 명세서](#api-명세서)
XI. [진행 상황](#진행-상황)
XII. [코드 스타일과 표준](#코드-스타일과-표준-)
XIII. [트러블 슈팅](#트러블-슈팅)
XIV. [개발 회고](#개발-회고)

## 주요 기능

### 비디오 업로드 및 스토리지 연동
- 사용자는 분석할 비디오 파일을 웹 애플리케이션을 통해 업로드할 수 있습니다.
- 업로드된 비디오 파일은 Amazon S3 스토리지에 안전하게 저장됩니다.
- Django 애플리케이션은 S3에 저장된 비디오 파일의 URL을 PySlowFast 모델에 전달합니다.

### PySlowFast 모델을 통한 비디오 분석
- Facebook AI Research에서 개발된 PySlowFast 모델을 활용하여 비디오 데이터를 분석합니다.
- 모델은 비디오 프레임에서 이상 행동 패턴을 감지하고 분류합니다.
- 감지된 이상 행동에 대한 좌표 정보와 관련 이미지를 생성합니다.

### 이상 행동 감지 및 결과 제공
- 시스템은 다음과 같은 이상 행동을 감지할 수 있습니다: 전도, 파손, 방화, 흡연, 유기, 절도, 폭행, 교통약자 위협 등.
- 감지된 이상 행동에 대한 결과는 JSON 형식으로 Django 애플리케이션에 반환됩니다.
- 결과에는 이상 행동 유형, 위치 좌표, 관련 이미지 경로 등의 정보가 포함됩니다.

### Django REST API를 통한 분석 결과 제공
- Django REST API를 통해 비디오 분석 결과를 클라이언트 애플리케이션에 제공합니다.
- API 엔드포인트를 호출하여 이상 행동 감지 결과를 실시간으로 가져올 수 있습니다.
- 분석 결과는 웹 애플리케이션, 모바일 앱 또는 타사 시스템에 통합될 수 있습니다.

## 기술 스택
Safe Eye 프로젝트는 다음과 같은 기술 스택을 활용하여 개발되고 있습니다:

개발환경 및 협업<br>
<img src="https://img.shields.io/badge/Visual Studio Code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white">  <img src="https://img.shields.io/badge/git-F05032?style=for-the-badge&logo=git&logoColor=white">
<img src="https://img.shields.io/badge/github-181717?style=for-the-badge&logo=github&logoColor=white">
<img src="https://img.shields.io/badge/discord-5865F2?style=for-the-badge&logo=discord&logoColor=white">

프론트엔드<br>
<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=white">  <img src="https://img.shields.io/badge/html5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
<img src="https://img.shields.io/badge/css3-1572B6?style=for-the-badge&logo=css3&logoColor=white">
<img src="https://img.shields.io/badge/tailwindcss-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white">
<img src="https://img.shields.io/badge/typescript-3178C6?style=for-the-badge&logo=typescript&logoColor=white">
<img src="https://img.shields.io/badge/nextdotjs-000000?style=for-the-badge&logo=nextdotjs&logoColor=white">
<img src="https://img.shields.io/badge/reactquery-007ACC?style=for-the-badge&logo=reactquery&logoColor=white">

백엔드<br>
<img src="https://img.shields.io/badge/python-3776AB?style=for-the-badge&logo=python&logoColor=white">  <img src="https://img.shields.io/badge/django-092E20?style=for-the-badge&logo=django&logoColor=white">
<img src="https://img.shields.io/badge/restframework-C5F74F?style=for-the-badge&logo=restframework&logoColor=white">
<img src="https://img.shields.io/badge/Graphene-EA4C89?style=for-the-badge&logo=Graphene&logoColor=white">

배포<br>
<img src="https://img.shields.io/badge/amazonaws-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white">  <img src="https://img.shields.io/badge/amazons3-569A31?style=for-the-badge&logo=amazons3&logoColor=white">
<img src="https://img.shields.io/badge/nginx-009639?style=for-the-badge&logo=nginx&logoColor=white">
<img src="https://img.shields.io/badge/gunicorn-499848?style=for-the-badge&logo=gunicorn&logoColor=white">

기타 라이브러리 <br>
데이터 처리 및 분석<br>
<img src="https://img.shields.io/badge/numpy-013243?style=for-the-badge&logo=numpy&logoColor=white">  <img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white">
<img src="https://img.shields.io/badge/scipy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white">


컴퓨터 비전 및 이미지 처리<br>
<img src="https://img.shields.io/badge/pytorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white">  <img src="https://img.shields.io/badge/CUDA-4285F4?style=for-the-badge&logo=CUDA&logoColor=white">
<img src="https://img.shields.io/badge/conda-44A833?style=for-the-badge&logo=conda&logoColor=white">
<img src="https://img.shields.io/badge/tensorflow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white">

## 시스템 아키텍처(오늘 배포되는것 까지만 만들어서 업데이트 예정)
[시스템 아키텍처 다이어그램 이미지]

I. 사용자가 웹 애플리케이션을 통해 비디오 파일을 업로드합니다.
II. 업로드된 비디오 파일은 Amazon S3 스토리지에 저장됩니다.
III. Django 애플리케이션은 S3에 저장된 비디오 파일의 URL을 PySlowFast 모델 API에 전송합니다.
IV. PySlowFast 모델은 비디오 데이터를 분석하고 이상 행동 감지 결과를 생성합니다.
V. 분석 결과는 Django 애플리케이션으로 반환되어 처리됩니다.
VI. 클라이언트 애플리케이션은 Django REST API를 호출하여 분석 결과를 가져옵니다.
VII. 분석 결과는 클라이언트 애플리케이션에 렌더링되어 사용자에게 표시됩니다.

## 라이센스
본 프로젝트는 오픈소스 소프트웨어를 활용하여 개발되었습니다. 사용된 주요 라이브러리 및 프레임워크의 라이센스 정보는 다음과 같습니다:

### PySlowFast
- 라이센스: Apache 2.0 License
- 저장소: https://github.com/facebookresearch/slowfast

### Django
- 라이센스: BSD 3-Clause License
- 저장소: https://github.com/django/django

### Django REST Framework
- 라이센스: BSD 3-Clause License
- 저장소: https://github.com/encode/django-rest-framework

### AWS SDK for Python (Boto3)
- 라이센스: Apache 2.0 License
- 저장소: https://github.com/boto/boto3

본 프로젝트의 소스 코드는 [라이센스 이름] 하에 공개되어 있습니다. 자세한 내용은 LICENSE 파일을 참조하시기 바랍니다.

## 기여
본 프로젝트는 오픈소스 기반으로 진행되었으며, 커뮤니티의 기여를 환영합니다. 버그 리포트, 기능 제안, 코드 기여 등은 언제든 환영입니다. 기여 방법은 CONTRIBUTING.md 파일을 참조하세요.

## 팀 소개

| 이혜림(팀장) | 이규성 | 전지용 | 정진영 | 박경민 |
| :---: | :---: | :---: | :---: | :---: |
| <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2F7baaf7f18e1c4f2a951cd0d7f1543f37" style="min-width: 170px; height: 200px; object-fit: cover;"> | <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2Feccac9ef755b40f3b864649e853f0aef" style="width: 170px; height: 200px; object-fit: cover;"> | <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2Fef610161c92e42148bc9d5fe85e92951" style="width: 170px; height: 200px; object-fit: cover;"> | <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2Fc24db93543b64f16b3234738fbfdcb4d" style="width: 170px; height: 200px; object-fit: cover;"> | <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2F84a7b4f5853a4f50a31e655aa3d5ab7c" style="min-width: 170px; height: 200px; object-fit: cover;"> |
| <a href="https://github.com/matty255"> 🌱 HY. Lee | <a href="https://github.com/rkawkclzls"> 🌱 rkawkclzls | <a href="https://github.com/mkdirlife"> 🌱 mkdirlife | <a href="https://github.com/najasinis"> 🌱 najasinis | <a href="https://github.com/Masterdual"> 🌱 Masterdual |
| 프로젝트의 아키텍처를 설계하고, 기획 단계에서 요구사항을 명확히 정의하며, 프론트엔드 개발을 담당 했습니다. | AI 모델의 출력값(이미지)을 저장하고 관리하는 미디어 앱을 작성하여 분석 결과를 효과적으로 활용할 수 있도록 했습니다. | utils 앱 개발을 담당하고 있습니다. 다른 애플리케이션에서 공통적으로 사용할 수 있는 기능을 제공했습니다. | accounts 앱 및 chat 앱 개발을 담당하고 있으며, 모델링을 분담하고 있습니다. 더불어 사용자 인증과 관련된 기능들(정보 관
