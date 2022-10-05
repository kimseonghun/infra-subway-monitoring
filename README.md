<p align="center">
    <img width="200px;" src="https://raw.githubusercontent.com/woowacourse/atdd-subway-admin-frontend/master/images/main_logo.png"/>
</p>
<p align="center">
  <img alt="npm" src="https://img.shields.io/badge/npm-%3E%3D%205.5.0-blue">
  <img alt="node" src="https://img.shields.io/badge/node-%3E%3D%209.3.0-blue">
  <a href="https://edu.nextstep.camp/c/R89PYi5H" alt="nextstep atdd">
    <img alt="Website" src="https://img.shields.io/website?url=https%3A%2F%2Fedu.nextstep.camp%2Fc%2FR89PYi5H">
  </a>
  <img alt="GitHub" src="https://img.shields.io/github/license/next-step/atdd-subway-service">
</p>

<br>

# 인프라공방 샘플 서비스 - 지하철 노선도

<br>

## 🚀 Getting Started

### Install
#### npm 설치
```
cd frontend
npm install
```
> `frontend` 디렉토리에서 수행해야 합니다.

### Usage
#### webpack server 구동
```
npm run dev
```
#### application 구동
```
./gradlew clean build
```
<br>


### 1단계 - 화면 응답 개선하기
1. 웹 성능예산은 어느정도가 적당하다고 생각하시나요. 이 때, 서버 목표 응답시간은 어떻게 되나요?

* 응답 개선 url : https://www.infra-subway-deploy.kro.kr/path
* 비교군 url : https://m.map.kakao.com/ (경쟁사 : 카카오맵)
* 성능 예산 : 모바일 기기의 Time to Interactive는 5초 미만 (경로 검색이 주요 핵심 도메인이라 판단했기 때문)
* 목표 응답 시간 : TTI 5초 미만

2. 성능 개선 결과를 공유해주세요

* 성능 개선 전 TTI : 15.2초
* gzip 적용 후 TTI : 7.2초 (대폭 개선)
   * <img src="./src/main/resources/static/images/perf/gzip_mobile.png" width="400" height="300" title="image2"/>
* http 2.0 && cache 적용 후 TTI : 7.0초 (소폭 개선)
   * <img src="./src/main/resources/static/images/perf/gzip-cache_mobile.png" width="400" height="300" title="image1">

3. 어떤 부분을 개선해보셨나요? 과정을 설명해주세요

* nginx에 gzip 적용
* nginx에 정적 리소스 cache 적용
   * 다만, 캐시 적용 됐는지가 의문 (nginx 캐시 저장 디렉토리가 비어있음)
* https 2.0 적용

---

### 2단계 - 부하 테스트 
1. 부하테스트 전제조건은 어느정도로 설정하셨나요

2. Smoke, Load, Stress 테스트 스크립트와 결과를 공유해주세요

---

### 3단계 - 스케일 아웃

1. Launch Template 링크를 공유해주세요.

2. cpu 부하 실행 후 EC2 추가생성 결과를 공유해주세요. (Cloudwatch 캡쳐)

```sh
$ stress -c 2
```

---

### [추가] 로깅, 모니터링
1. 각 서버내 로깅 경로를 알려주세요

2. Cloudwatch 대시보드 URL을 알려주세요
---

### [추가] WAS 개선하기
1. 성능 개선 결과를 공유해주세요 (Smoke, Load, Stress 테스트 결과)

2. 어떤 부분을 개선해보셨나요? 과정을 설명해주세요
