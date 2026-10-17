# INFRIUM | GitHub 협업 규칙

> IoT·AI 기반 교량 구조 상태 모니터링 및 디지털 트윈 시스템

## 1. 프로젝트 개요

INFRIUM은 ESP32 기반 센서 데이터 수집, AI 이상 탐지, 구조 상태 분류, 위험도 평가, Django 백엔드 및 3D 디지털 트윈을 결합한 교량 모니터링 프로젝트입니다.

### GitHub Repository

| 파트 | Repository | 주요 역할 |
|---|---|---|
| HW | [HW](https://github.com/INFRIUM/HW) | ESP32 및 센서 데이터 수집 |
| AI① | [AI-1](https://github.com/INFRIUM/AI-1) | Isolation Forest 이상 탐지 |
| AI② | [AI-2](https://github.com/INFRIUM/AI-2) | XGBoost 구조 상태 분류 및 위험도 계산 |
| BE | [BE](https://github.com/INFRIUM/BE) | Django API 및 데이터 관리 |
| FE | [FE](https://github.com/INFRIUM/FE) | 모니터링 대시보드 및 3D 디지털 트윈 |

---

## 2. 기본 협업 원칙

1. `main`, `develop` 브랜치에서 직접 개발하거나 Push하지 않습니다.
2. 기능 개발 및 버그 수정 전 GitHub Issue를 생성합니다.
3. Issue 번호를 기준으로 작업 브랜치를 생성합니다.
4. 작업 브랜치는 최신 `develop`을 기준으로 생성합니다.
5. Commit Convention에 맞춰 Commit합니다.
6. GitHub에 Push한 뒤 `develop`으로 Pull Request(PR)를 생성합니다.
7. 변경 사항과 테스트 결과를 확인한 후 담당자가 직접 Merge할 수 있습니다.
8. 코드 리뷰는 권장하지만 필수 승인 인원은 0명입니다.
9. Merge 완료된 작업 브랜치는 삭제합니다.
10. API·DB·데이터 형식 변경 시 연관 파트와 사전에 협의합니다.
11. 인증정보, 비밀번호, 비공개 데이터는 GitHub에 업로드하지 않습니다.
12. 각 파트의 기능 개발 후 전체 시스템 통합 테스트를 진행합니다.

### 기본 개발 흐름

```text
Issue 생성
    ↓
작업 브랜치 생성
    ↓
기능 개발
    ↓
Commit
    ↓
Push
    ↓
develop으로 PR 생성
    ↓
변경 사항 및 테스트 확인
    ↓
Merge
    ↓
통합 테스트
    ↓
develop → main PR
    ↓
안정 버전 반영
```

---

## 3. Branch Convention

### 3.1 브랜치 역할

| 브랜치 | 역할 |
|---|---|
| `main` | 검증된 안정 버전 |
| `develop` | 기능 통합 및 테스트 |
| `feature/*` | 새로운 기능 개발 |
| `fix/*` | 버그 수정 |
| `refactor/*` | 코드 리팩토링 |
| `docs/*` | 문서 작업 |
| `test/*` | 테스트 작업 |
| `hotfix/*` | 긴급 오류 수정 |

### 3.2 브랜치 이름

형식:

`유형/이슈번호-기능명`

예시:

```text
feature/1-esp32-sensor
feature/2-vibration-collection
feature/3-isolation-forest
feature/4-xgboost-classification
feature/5-risk-score
feature/6-django-api
feature/7-digital-twin

fix/8-sensor-data-error
refactor/9-risk-calculation
docs/10-api-spec
test/11-integration-test
hotfix/12-server-error
```

### 3.3 브랜치 규칙

- 하나의 Issue당 하나의 작업 브랜치를 사용하는 것을 원칙으로 합니다.
- 작업 브랜치는 최신 `develop`에서 생성합니다.
- 브랜치 이름은 영문 소문자, 숫자, 하이픈을 사용합니다.
- 브랜치 이름에 `#`을 포함하지 않습니다.
- Issue 번호는 Repository마다 독립적으로 관리됩니다.
- 다른 팀원의 브랜치를 임의로 수정하거나 삭제하지 않습니다.

---

## 4. Commit Convention

### 4.1 Commit 유형

| 유형 | 설명 |
|---|---|
| ✨ `feat` | 새로운 기능 추가 |
| 🐛 `fix` | 버그 수정 |
| 📝 `docs` | 문서 작성 및 수정 |
| ♻️ `refactor` | 코드 리팩토링 |
| 💄 `style` | 코드 스타일 및 UI 수정 |
| ✅ `test` | 테스트 코드 추가 및 수정 |
| 🚀 `chore` | 환경설정 및 패키지 관리 |
| 🚑 `hotfix` | 긴급 오류 수정 |

### 4.2 Commit 형식

```text
[이모지 type #이슈번호]: 작업 내용
```

### 4.3 파트별 예시

**HW**

```text
[✨ feat #1]: ESP32 진동 센서 데이터 수집 기능 구현
[✨ feat #2]: 센서 데이터 전송 기능 구현
```

**AI①**

```text
[✨ feat #1]: 진동 데이터 전처리 기능 구현
[✨ feat #2]: 진동 특징값 추출 기능 구현
[✨ feat #3]: Isolation Forest 이상 탐지 모델 구현
```

**AI②**

```text
[✨ feat #1]: XGBoost 구조 상태 분류 기능 구현
[✨ feat #2]: RiskScore 계산 로직 구현
[✨ feat #3]: 위험도 4단계 판정 기능 구현
```

**BE**

```text
[✨ feat #1]: Django 센서 데이터 수신 API 구현
[✨ feat #2]: AI 분석 결과 저장 기능 구현
```

**FE**

```text
[✨ feat #1]: 교량 상태 모니터링 대시보드 구현
[✨ feat #2]: 3D 디지털 트윈 시각화 구현
```

**기타**

```text
[🐛 fix #5]: 센서 데이터 누락 처리 오류 수정
[📝 docs #6]: AI① AI② 데이터 전달 명세 업데이트
[♻️ refactor #7]: 위험도 계산 함수 분리
[💄 style #8]: 대시보드 상태 표시 UI 수정
[✅ test #9]: RiskScore 계산 단위 테스트 추가
[🚀 chore #10]: FastAPI 개발 환경 설정
```

### 4.4 Commit 주의사항

- 실제 수정 내용을 구체적으로 작성합니다.
- 서로 관련 없는 기능을 하나의 Commit에 포함하지 않습니다.
- Commit 전 `git status`, `git diff`를 확인합니다.
- 인증정보 및 불필요한 파일이 포함되지 않았는지 확인합니다.

---

## 5. Issue Convention

### 5.1 Issue 생성 기준

다음 작업을 시작하기 전에 Issue를 생성합니다.

- 새로운 기능 개발
- 버그 수정
- 코드 리팩토링
- 문서 작성 및 수정
- API 연동
- 테스트 및 기능 검증

### 5.2 Issue 제목 형식

`[파트] 작업 내용`

예시:

```text
[HW] ESP32 진동 센서 데이터 수집 기능 구현
[AI1] Isolation Forest 이상 탐지 모델 구현
[AI2] XGBoost 구조 상태 분류 기능 구현
[AI2] RiskScore 계산 로직 구현
[BE] AI 분석 결과 저장 API 구현
[FE] 3D 디지털 트윈 시각화 구현
```

### 5.3 Issue 작성 항목

1. 작업 개요
2. 작업 목적
3. 세부 작업
4. 연관 파트
5. 예상 결과물
6. 완료 기준

### 5.4 Issue 작성 예시

**제목:** `[AI2] RiskScore 계산 로직 구현`

```text
작업 개요:
XGBoost 구조 상태 분류 결과와 진동 변화 지표를 활용하여
RiskScore를 계산하는 기능을 구현합니다.

작업 목적:
교량 구조 상태를 0~100 위험도 점수와
정상·주의·경고·위험 4단계로 표현합니다.

세부 작업:
- XGBoost 구조 상태 분류 결과 처리
- 정상 대비 진동 변화량 계산
- RiskScore 계산식 구현
- 위험도 단계 판정
- FastAPI 응답 형식 구성
- 단위 테스트

연관 파트:
AI①, BE, FE

예상 결과물:
RiskScore 계산 함수, 위험도 판정 함수, 테스트 결과

완료 기준:
- RiskScore가 0~100 범위로 계산됨
- 위험도 4단계 판정 정상 동작
- API 응답 형식 검증 완료
- 관련 테스트 통과
```

---

## 6. Pull Request Convention

### 6.1 PR 대상 브랜치

기능 개발 완료:

```text
feature/* → develop
```

통합 테스트 완료:

```text
develop → main
```

### 6.2 PR 제목

형식:

`[#이슈번호] 작업 내용`

예시:

```text
[#1] ESP32 진동 데이터 수집 기능 구현
[#2] Isolation Forest 이상 탐지 모델 구현
[#3] XGBoost 구조 상태 분류 기능 구현
[#4] RiskScore 계산 기능 구현
[#5] Django 분석 결과 저장 API 구현
[#6] 3D 디지털 트윈 시각화 구현
```

### 6.3 PR 작성 항목

1. 관련 Issue
2. 작업 내용
3. 테스트 결과
4. 연관 파트
5. 실행 화면 또는 결과
6. 참고사항

### 6.4 PR 예시

```text
작업 내용:
- XGBoost 구조 상태 분류 결과 처리
- RiskScore 계산 로직 구현
- 위험도 4단계 판정 기능 추가

관련 Issue:
Related to #4

테스트 결과:
- RiskScore 범위 테스트 통과
- 위험도 단계 판정 테스트 통과
- FastAPI 응답 테스트 통과

연관 파트:
AI①, BE, FE

참고사항:
위험도 계산식 및 Threshold는 실험 결과에 따라 조정될 수 있습니다.
```

### 6.5 Merge 규칙

- `main`, `develop`에 직접 Push하지 않습니다.
- PR 생성 전 관련 테스트를 진행합니다.
- 다른 팀원의 코드 리뷰를 권장합니다.
- 필수 승인 인원은 0명으로 운영합니다.
- 담당자는 변경 사항과 테스트 결과를 확인한 뒤 직접 Merge할 수 있습니다.
- API 및 데이터 형식 변경 시 연관 파트와 협의합니다.
- 테스트 실패 상태에서 임의로 Merge하지 않습니다.
- Merge 완료된 작업 브랜치는 삭제합니다.

**Issue 자동 종료 주의사항:** `develop`으로 병합한 PR에서는 `Closes #번호`가 Issue를 자동 종료하지 않을 수 있습니다. 완료 여부를 확인한 뒤 수동 종료하거나 최종 `main` 병합 시 종료합니다.

---

## 7. Git 작업 절차

아래 명령어는 로컬 Repository 연결이 완료된 상태에서 사용합니다.

### 7.1 작업 시작

```bash
git status
git branch --show-current

git switch develop
git pull --ff-only origin develop

git switch -c feature/3-isolation-forest
```

### 7.2 작업 완료

```bash
git status
git diff

git add .

git diff --cached

git commit -m "[✨ feat #3]: Isolation Forest 이상 탐지 모델 구현"

git push -u origin feature/3-isolation-forest
```

### 7.3 Pull Request

GitHub에서 다음과 같이 설정합니다.

```text
base: develop
compare: feature/3-isolation-forest
```

### 7.4 Merge 완료 후

```bash
git switch develop
git pull --ff-only origin develop

git branch -d feature/3-isolation-forest
```

※ 기존 로컬 프로젝트에 Git 이력이 있는 경우 원격 Repository 연결 전 상태를 확인해야 합니다. 특히 AI-2의 기존 개발 파일과 Git 이력을 임의로 초기화하지 않습니다.

---

## 8. 파트 간 연동 규칙

### 8.1 주요 시스템 흐름

```text
HW (ESP32 + 센서)
        ↓
센서 데이터 수신
        ↓
AI① 전처리 및 특징값 추출
        ↓
AI① Isolation Forest 이상 탐지
        ↓
AI② XGBoost 구조 상태 분류
        ↓
AI② RiskScore 및 위험도 단계 계산
        ↓
Django Backend
        ↓
Frontend 대시보드 및 3D 디지털 트윈
```

※ 위 흐름은 주요 분석 과정을 단순화한 것입니다. 실제 데이터 수신 및 API 호출 경로는 파트 간 API 명세서에 따릅니다.

### 8.2 파트별 주요 데이터

**HW**
- ESP32 센서 측정 데이터
- 측정 시각
- 센서 종류 및 측정 단위

**AI①**
- 원시 센서 데이터
- 진동 특징값
- Isolation Forest 이상 탐지 결과

**AI②**
- XGBoost 구조 상태 분류 결과
- RiskScore(0~100)
- 정상·주의·경고·위험 4단계 결과

**BE**
- 센서 데이터 저장 및 관리
- AI 분석 결과 저장
- 프론트엔드 API 제공

**FE**
- 센서 데이터 시각화
- 위험도 점수 및 단계 표시
- 3D 디지털 트윈

### 8.3 API 변경 절차

1. API 변경 Issue 생성
2. 연관 파트 담당자에게 공유
3. 요청·응답 데이터 형식 협의
4. API 명세서 업데이트
5. 코드 구현 및 테스트
6. Pull Request 생성
7. 연관 파트 확인 후 Merge

### 8.4 사전 협의가 필요한 변경

- HW 센서 데이터 형식 변경
- AI① 특징값 및 이상 탐지 결과 구조 변경
- AI② 구조 상태 및 RiskScore 응답 형식 변경
- Django API URL 및 JSON 필드명 변경
- DB 테이블 및 컬럼 변경
- FE 디지털 트윈 데이터 형식 변경

**API URL, JSON 필드명, 데이터 타입 및 측정 단위는 임의로 변경하지 않습니다.**

---

## 9. AI 모델 및 데이터 관리

### 9.1 AI①

- 센서 데이터 전처리
- 진동 특징값 추출
- Isolation Forest 이상 탐지
- AI② 연동 데이터 생성

### 9.2 AI②

- XGBoost 구조 상태 분류
- `NORMAL`, `D1`, `D2`, `D3` 분류
- 별도 계산식을 통한 RiskScore 산출
- 정상·주의·경고·위험 4단계 판정
- FastAPI 기반 분석 기능 제공

**주의:** XGBoost가 RiskScore를 직접 회귀 예측하는 구조로 임의 변경하지 않습니다.

### 9.3 업로드 가능한 파일

- 학습 및 추론 코드
- 전처리 코드
- 모델 설정 파일
- `requirements.txt`
- 테스트 코드
- 모델 평가 결과 요약
- 데이터셋 설명 문서
- 재배포가 허용된 소규모 샘플 데이터

### 9.4 일반 Git 업로드 제한

- 대용량 원시 센서 데이터
- 대용량 학습 데이터셋
- 대용량 모델 가중치
- 재배포 권한이 없는 데이터
- 인증정보가 포함된 파일

### 9.5 버전 관리

- 모델 버전 기록
- 학습 데이터 버전 기록
- 모델 평가 결과 기록
- RiskScore 계산식 변경 이력 기록
- 위험도 Threshold 변경 근거 기록
- 대용량 파일은 Git LFS 또는 별도 저장소 활용 검토

---

## 10. 테스트 및 통합 검증

### 10.1 파트별 테스트

| 파트 | 테스트 내용 |
|---|---|
| HW | 센서 측정 및 데이터 전송 |
| AI① | 전처리·특징값 추출·이상 탐지 |
| AI② | 구조 상태 분류·RiskScore·위험도 단계 |
| BE | API·DB 저장 및 조회 |
| FE | 대시보드·위험도 표시·3D 디지털 트윈 |

### 10.2 통합 테스트

```text
HW → AI① → AI② → BE → FE
```

검증 항목:

- 센서 데이터 정상 전달 여부
- AI① 이상 탐지 결과 전달 여부
- AI② 구조 상태 및 위험도 계산 여부
- Django 분석 결과 저장 여부
- FE 대시보드 및 디지털 트윈 표시 여부

### 10.3 테스트 원칙

- PR 생성 전 관련 기능 테스트
- API 변경 시 연관 파트 연동 테스트
- 테스트 결과 PR에 기록
- 오류 발생 시 수정 후 Merge
- 최종 시연 전 전체 시스템 통합 테스트

---

## 11. 보안 규칙

### 11.1 GitHub 업로드 금지

- `.env`
- `.env.local`
- `.env.production`
- API Key
- DB 비밀번호
- Secret Key
- 인증 토큰
- 비공개 데이터
- 재배포 권한이 없는 데이터셋

### 11.2 필수 보안 원칙

- `.gitignore`를 확인합니다.
- 실제 인증정보는 환경변수로 관리합니다.
- `.env.example`에는 실제 인증정보를 입력하지 않습니다.
- Issue와 PR에 비밀정보가 포함된 로그를 첨부하지 않습니다.
- 인증정보가 노출되면 즉시 폐기 및 재발급합니다.
- Commit 전 변경 파일을 확인합니다.

---

## 12. 최종 협업 원칙

- [x] `main`, `develop` 직접 개발 금지
- [x] Issue 기반 작업 관리
- [x] Issue 번호 기반 브랜치 생성
- [x] Commit Convention 준수
- [x] `develop` 대상 PR 생성
- [x] Merge 전 테스트 확인
- [x] 필수 승인 없이 담당자 직접 Merge 가능
- [x] API 및 데이터 형식 변경 시 사전 협의
- [x] AI 모델 및 데이터 버전 관리
- [x] 인증정보 업로드 금지
- [x] 파트별 개발 완료 후 통합 테스트

---

**INFRIUM 팀원은 본 협업 규칙을 기준으로 GitHub 작업을 진행합니다.**
