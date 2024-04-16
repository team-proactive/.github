# Safe-Eye: 비디오 감시 및 이상 행동 감지 시스템

Safe-Eye는 PySlowFast 모델과 Django 웹 프레임워크를 활용한 비디오 감시 및 이상 행동 감지 시스템입니다. 이 프로젝트는 CCTV 또는 보안 카메라에서 수집된 비디오 데이터를 실시간으로 분석하여 잠재적인 위험 상황을 탐지하고 대응할 수 있도록 설계되었습니다.

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

## 기술 스택(백엔드, 프론트엔드)
- 프론트엔드(링크)
- PySlowFast: Facebook AI Research에서 개발한 비디오 분석 모델
- Django: 웹 애플리케이션 프레임워크
- Django REST Framework: API 개발을 위한 툴킷
- Amazon S3: 클라우드 스토리지 서비스
- React (또는 Vue.js): 프론트엔드 프레임워크 (선택적)

## 시스템 아키텍처(오늘 배포되는것 까지만 만들어서 업데이트 예정)
[시스템 아키텍처 다이어그램 이미지]

1. 사용자가 웹 애플리케이션을 통해 비디오 파일을 업로드합니다.
2. 업로드된 비디오 파일은 Amazon S3 스토리지에 저장됩니다.
3. Django 애플리케이션은 S3에 저장된 비디오 파일의 URL을 PySlowFast 모델 API에 전송합니다.
4. PySlowFast 모델은 비디오 데이터를 분석하고 이상 행동 감지 결과를 생성합니다.
5. 분석 결과는 Django 애플리케이션으로 반환되어 처리됩니다.
6. 클라이언트 애플리케이션은 Django REST API를 호출하여 분석 결과를 가져옵니다.
7. 분석 결과는 클라이언트 애플리케이션에 렌더링되어 사용자에게 표시됩니다.

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
| <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2F7baaf7f18e1c4f2a951cd0d7f1543f37" style="display: block; margin: 0 auto; width: 200px; height: 200px; object-fit: cover;"> | <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2Feccac9ef755b40f3b864649e853f0aef" style="display: block; margin: 0 auto; width: 200px; height: 200px; object-fit: cover;"> | <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2Fef610161c92e42148bc9d5fe85e92951" style="display: block; margin: 0 auto; width: 200px; height: 200px; object-fit: cover;"> | <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2Fc24db93543b64f16b3234738fbfdcb4d" style="display: block; margin: 0 auto; width: 200px; height: 200px; object-fit: cover;"> | <img src="https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2F84a7b4f5853a4f50a31e655aa3d5ab7c" style="display: block; margin: 0 auto; width: 200px; height: 200px; object-fit: cover;"> |
| <a href="https://github.com/matty255"> 🌱 HY. Lee | <a href="https://github.com/rkawkclzls"> 🌱 rkawkclzls | <a href="https://github.com/mkdirlife"> 🌱 mkdirlife | <a href="https://github.com/najasinis"> 🌱 najasinis | <a href="https://github.com/Masterdual"> 🌱 Masterdual |
| 프로젝트의 아키텍처를 설계하고, 기획 단계에서 요구사항을 명확히 정의하며, 프론트엔드 개발을 담당 했습니다. | AI 모델의 출력값(이미지)을 저장하고 관리하는 미디어 앱을 작성하여 분석 결과를 효과적으로 활용할 수 있도록 했습니다. | utils 앱 개발을 담당하고 있습니다. 다른 애플리케이션에서 공통적으로 사용할 수 있는 기능을 제공했습니다. | accounts 앱 및 chat 앱 개발을 담당하고 있으며, 모델링을 분담하고 있습니다. 더불어 사용자 인증과 관련된 기능들(정보 관리, 권한 부여 등), 채팅방 생성 기능, 실시간 채팅 기능들을 구현했습니다. | alarm 앱 개발을 담당했습니다. 적절한 경고 메시지를 커스텀하고, DB에 저장할 수 있도록 했습니다. |



## 주요 기능

Safe Eye 프로젝트는 다음과 같은 주요 기능을 제공할 예정입니다:

1. 실시간 이상 행동 감지

   - CCTV 영상에서 사람들의 행동을 실시간으로 분석하여 이상 행동을 감지합니다.
   - 폭력, 절도, 기물 파손 등 다양한 유형의 이상 행동을 인식할 수 있습니다.
   - 이상 행동 발생 시 즉각적인 알람을 발송하여 신속한 대응을 촉진합니다.

2. 상세 분석 화면

   - 선택한 카메라 또는 영역의 고해상도 비디오 피드를 제공합니다.
   - 감지된 이벤트 목록과 상세 정보를 확인할 수 있습니다.
   - 사용자 메모 및 설명을 추가할 수 있는 기능을 제공합니다.
   - 비디오 클립, 스크린샷, 이벤트 데이터를 내보낼 수 있습니다.

3. 경고 및 알람 설정

   - 경고 및 알람 수준에 따른 특정 작업을 설정할 수 있습니다.
   - 생성형 AI 모델을 활용하여 맥락에 적합한 경고 및 알람 메시지를 자동으로 생성합니다.
   - 사용자가 알림 메시지와 수신자 목록을 사용자 정의할 수 있습니다.
   - 정기적인 테스트와 훈련을 예약할 수 있는 기능을 제공합니다.

4. 통계 및 보고 기능

   - 기간별 이벤트에 대한 상세 보고서를 생성합니다.
   - 이벤트 데이터를 필터링하고 정렬할 수 있는 옵션을 제공합니다.
   - 통계 데이터, 이벤트 로그, 보고서를 내보낼 수 있습니다.
   - 자동으로 보고서를 생성하고 전달하도록 예약할 수 있습니다.

5. 사용자 관리 및 설정
   - 사용자 프로필 정보를 업데이트하고 알림 기본 설정을 변경할 수 있습니다.
   - 시스템 상태를 모니터링하고 진단할 수 있는 도구를 제공합니다.
   - 각 사용자의 상태에 따라 알람을 분류합니다.

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

## 데이터베이스 모델링(ER Diagram)
![alt text](https://cdn.builder.io/api/v1/image/assets%2F253795ae855443f2bcf20ffa08f40a29%2Fa2c403b4d3b140178ee7e0127531b31f)
- AbstractBaseUser 테이블 : 사용자 인증을 위한 기본 필드를 제공하는 추상 모델입니다.
- PermissionsMixin 테이블 : 사용자 권한 관련 필드를 제공하는 믹스인 클래스입니다. AbstractUser 모델에서 해당 믹스인을 사용하여 권한 관련 기능을 추가합니다.
- AbstractUser 테이블 : User 모델의 기반이 되는 추상 사용자 모델입니다. AbstractBaseUser와 PermissionsMixin을 상속받아 구현되었습니다.
- User 테이블 : Django의 기본 User 모델입니다. 사용자 정보를 저장하는 역할을 합니다. AbstractUser를 상속받아 구현되었습니다.
- CustomUser 테이블 : User 모델을 상속받아 확장한 커스텀 사용자 모델입니다. User 모델의 필드를 포함하면서 추가적인 필드(bio, profile_name 등)를 가지고 있습니다.
- Group 테이블 : 사용자 그룹 정보를 저장하는 테이블입니다. User 테이블과 다대다 관계를 가지고 있습니다.
- Permission 테이블 : 권한 정보를 저장하는 테이블입니다. ContentType 테이블과 외래 키 관계를 가지고 있습니다.
- ContentType 테이블 : Django의 ContentType 프레임워크에서 사용되는 테이블입니다. 모델 클래스를 식별하기 위한 정보를 저장합니다. 
                      Permission 테이블과 LogEntry 테이블에서 외래 키로 사용됩니다.
- Content 테이블 : 컨텐츠 정보를 저장하는 테이블입니다. User 테이블과 ContentType 테이블과 외래 키 관계를 가지고 있습니다.
- LogEntry 테이블 : Django의 Admin 로그 정보를 저장하는 테이블입니다. User 테이블과 ContentType 테이블과 외래 키 관계를 가지고 있습니다.
- AbstractBaseSession 테이블 : Session 모델의 기반이 되는 추상 세션 모델입니다. Session 모델에서 공통적으로 사용되는 필드를 정의합니다.
- Session 테이블 : 사용자의 세션 정보를 저장하는 테이블입니다. AbstractBaseSession을 상속받아 구현되었습니다.
- OutstandingToken 테이블 : Django REST framework의 토큰 인증 방식에서 사용되는 테이블입니다. User 테이블과 외래 키 관계를 가지고 있습니다.
- BlacklistedToken 테이블 : 블랙리스트에 등록된 토큰 정보를 저장하는 테이블입니다. OutstandingToken 테이블과 외래 키 관계를 가지고 있습니다.
- Site 테이블 : Django의 Site 프레임워크에서 사용되는 테이블입니다. 웹사이트의 도메인과 이름을 저장합니다.

## 진행 상황

저희 팀은 현재까지 다음과 같은 작업을 진행했습니다:

1. 프로젝트 아키텍처 설계 및 기획

   - 프로젝트의 전반적인 아키텍처를 설계하고, 필요한 기능과 요구사항을 정의했습니다.
   - 각 구성 요소 간의 상호 작용과 데이터 흐름을 고려하여 시스템 구조를 설계했습니다.

2. 백엔드 앱 구조 설계 및 개발

   - Django 프레임워크를 사용하여 백엔드 애플리케이션의 기본 구조를 설계했습니다.
   - accounts, utils, media, alarm, notice 등의 앱을 생성하고, 각 앱의 모델과 API 엔드포인트를 개발했습니다.

3. 프론트엔드 개발 환경 구축 및 초기 화면 개발
   - Next.js 프레임워크를 사용하여 프론트엔드 개발 환경을 구축했습니다.
   - 초기 화면 디자인을 작성하고, 컴포넌트 기반으로 UI를 개발하기 시작했습니다.

또한, 저희 팀은 GitHub의 이슈 템플릿, 위키, 프로젝트 기능을 활용하여 효율적으로 프로젝트를 관리하고 있습니다. 실시간 소통과 협업은 디스코드를 사용합니다.


## 코드 스타일과 표준 🚀🚀🚀

이 프로젝트에서는 일관되고 가독성 높은 코드를 유지하기 위해 다음과 같은 코드 스타일 가이드와 표준을 따릅니다.

### 코드 스타일[코드 스타일 가이드](https://github.com/team-proactive/safe-eye/wiki/%EC%BB%A8%EB%B2%A4%EC%85%98-%EA%B0%80%EC%9D%B4%EB%93%9C-Overview)
PEP 8을 기반으로 한 파이썬 코드 스타일 가이드를 준수합니다.
들여쓰기는 공백 4칸을 사용합니다.
변수와 함수 이름은 스네이크 케이스를 사용합니다.
클래스 이름은 파스칼 케이스를 사용합니다.
한 줄의 최대 길이는 88자로 제한합니다.
불필요한 공백을 사용하지 않습니다.
연산자 앞뒤로 공백을 사용합니다.
함수와 클래스 사이에는 두 줄의 공백을 사용합니다.

### 코드 포매팅
Black 포매터를 사용하여 코드 스타일을 자동으로 통일합니다.
Black의 기본 설정을 그대로 사용합니다.
에디터에서 저장 시 자동으로 포매팅되도록 설정하는 것을 권장합니다.

### 커밋 메시지 컨벤션
커밋 메시지는 다음과 같은 형식을 따릅니다.

✨ Feat: 새로운 기능 추가
🐛 Fix: 버그 수정
📚 Docs: 문서 변경
🎨 Style: 코드 스타일 변경 (코드 동작에 영향을 주지 않는 변경사항)
♻️ Refactor: 코드 리팩토링
✅ Test: 테스트 코드 추가 또는 수정
🔧 Chore: 빌드 관련 파일 수정, 패키지 매니저 설정 등

커밋 제목은 기능을 설명할 수 있게 간결하게 작성합니다.

## 트러블 슈팅

미디어 앱 개발 과정에서 다음과 같은 다양한 이슈들이 발생했으며, 이를 해결하는 과정에서 많은 경험과 교훈을 얻을 수 있었습니다.

### 1. 스토리지 설정 이슈

- 문제 상황: Django 개발 서버에서 정적 파일과 미디어 파일을 제대로 서빙하지 못하는 문제가 발생했습니다.
- 해결 방법:
  1. `settings.py` 파일에서 `STATIC_ROOT`, `STATIC_URL`, `MEDIA_ROOT`, `MEDIA_URL` 등의 설정을 적절히 수정했습니다.
  2. 프로덕션 환경에서는 Amazon S3와 같은 객체 스토리지를, 로컬 환경에서는 파일 시스템을 사용하도록 설정했습니다.
  3. `storages` 라이브러리를 활용하여 Django와 S3 스토리지를 연동했습니다.
- 결과: 정적 파일과 미디어 파일을 안전하게 관리할 수 있게 되었습니다. 프로덕션 환경에서는 S3 스토리지를 활용하여 파일 관리의 확장성과 안정성을 확보했습니다.
- 배운 점: 프로젝트 설정 단계에서 파일 저장 및 관리 전략을 세우는 것이 중요합니다. 프로덕션 환경과 개발 환경에 따라 다른 접근 방식이 필요할 수 있으므로, 상황에 맞는 적절한 설정을 해야 합니다.

### 2. 이미지 업로드 및 표시 이슈

- 문제 상황: 사용자가 업로드한 이미지를 서버에 저장하고, 웹 페이지에 표시하는 과정에서 여러 가지 문제가 발생했습니다.
- 해결 방법:
  1. 이미지 업로드 시 파일 형식, 크기, 해상도 등을 검증하는 로직을 구현했습니다.
  2. 업로드된 이미지 파일명을 고유한 값으로 변경하여 중복 문제를 해결했습니다.
  3. 이미지 썸네일 생성 기능을 추가하여 원본 이미지와 썸네일 이미지를 모두 저장했습니다.
  4. 웹 페이지에 이미지를 표시할 때 적절한 크기로 조정하고, 로딩 속도를 개선하는 작업을 수행했습니다.
- 결과: 안전하고 효율적인 이미지 업로드 및 표시 기능을 구현할 수 있었습니다.
- 배운 점: 이미지 처리는 복잡한 작업이므로, 보안, 성능, 사용자 경험 등 다양한 측면을 고려해야 합니다. 이를 위해 적절한 라이브러리와 기술을 활용하고, 테스트와 최적화 작업을 수행해야 합니다.

위와 같이 다양한 이슈를 해결하면서 실무 프로젝트 개발 경험을 쌓을 수 있었습니다. 특히 파일 관리, 이미지 처리, 보안, 성능 최적화 등의 측면에서 많은 지식과 기술을 습득할 수 있었습니다.


## 맺음말

프로젝트를 진행하면서 많은 것을 배우고 성장하고 있습니다. 팀원들 간의 협업과 소통을 통해 시너지를 내고, 어려움을 함께 극복해 나가고 있습니다. 이 과정에서 얻은 경험과 지식은 향후 저희의 발전에 소중한 자산이 될 것입니다.

Safe Eye 프로젝트가 성공적으로 완료되어 언젠가 실제 현장에서 이러한 기술을 적용할 때 도움이 되기를 희망합니다. 여러분의 관심과 응원이 저희에게 큰 힘이 될 것입니다. 함께 더 안전한 사회를 만드는 게발자가 되고 싶습니다.

감사합니다!
