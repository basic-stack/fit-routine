# Frontend 규칙

## 기본 규칙

코드 포맷팅 도구로 `Prettier 3.5.3`를, 린트 규칙 도구로 `ESLint 9.27.0`를 사용합니다. 즉, 프론트 규칙은 이 두 도구에 의존합니다. 상세한 설정은 다음을 참고하세요:

- https://github.com/basic-stack/fit-routine-frontend/blob/main/.prettierrc
- https://github.com/basic-stack/fit-routine-frontend/blob/main/eslint.config.mjs

### 폴더 이름 규칙

폴더 내 `jsx` 파일이 하나만 있는 경우, 해당 파일의 이름을 폴더의 이름으로 합니다. 그 외의 경우엔 소문자로 명명합니다.

### CSS 규칙

**CSS Module** 방식을 사용합니다. 즉, 모든 파일은 `module.css`로 끝나야 하며 태그가 직접 클래스를 지정해야 합니다.

## import 규칙

### 순서

import 선언 순서는 다음과 같습니다:

1. 외부 라이브러리
2. 내부 모듈
3. 내부 컴포넌트
4. 내부 유틸리티 
5. 내부 스타일

### 경로

절대 경로를 사용합니다. 단, 해당 컴포넌트에 대응하는 CSS 파일은 상대 경로를 사용합니다.

예시는 다음과 같습니다:
```javascript

// 절대 경로
import { isLoggedIn } from 'utils/helpers/token';

// 상대 경로
import styles from './LoginPage.module.css';
```