# Git 규칙

[GitHub Flow](https://docs.github.com/ko/get-started/using-github/github-flow)를 기본 규칙으로 합니다.

## 브랜치 명

**kebab-case**를 사용합니다. 브랜치 네임스페이스는 변경의 성격에 따라 짓습니다. 예시는 다음과 같습니다.

- `feature/` 기능 추가
- `refactor/` 코드 개선
- `docs/` 문서 추가
- `fix/` 긴급 수정

## 커밋 메세지

기능 중심으로 간결히 작성합니다. 예시는 다음과 같습니다.

- 소셜 로그인 추가
- 빈 쿼리 전달 시 500 에러 수정
- 설치 가이드 보강
- AuthService 분리

## Pull Request 규칙

### 코드 리뷰

**오전 12시**에 한 번, **오후 5시**에 한 번 모여 누적된 `Pull Request`에 대한 코드 리뷰를 진행하고 `main` 브랜치에 병합합니다. 단, 핫픽스에 대한 `Pull Reuqest`의 경우,
바로 코드 리뷰 진행 후 병합하도록 합니다.

### 충돌 규칙

가능한 경우 `git rebase`를 통해 해결합니다. 해결할 수 없는 경우 대신 `git merge`를 통해 해결합니다.

### 수정사항이 생겼을 경우

간단한 수정 시 PR브랜치에 수정 후 push해서 바로 수정을 하고, 대규모 수정 시 새 브랜치에서 수정 후 새 PR올려서 다음 코드리뷰 때 병합
