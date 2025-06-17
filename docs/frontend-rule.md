# Frontend 규칙

## 기본 규칙

코드 포맷팅 도구로 `Prettier 3.5.3`를, 린트 규칙 도구로 `ESLint 9.27.0`를 사용합니다. 즉, 프론트 규칙은 이 두 도구에 의존합니다. 상세한 설정은 다음을 참고하세요:

- https://github.com/basic-stack/fit-routine-frontend/blob/main/.prettierrc
- https://github.com/basic-stack/fit-routine-frontend/blob/main/eslint.config.mjs

### 변수/메소드/클래스명 네이밍 규칙

기본적으로 camelCase를 사용해야 한다.

### 파일 이름 규칙

기본적으로 PascalCase사용하여 작성한다. 예를 들어 `MainPage.jsx / Header.jsx`.

### 폴더 이름 규칙

기본적으로 소문자를 사용하고, 동일한 이름의 파일이 존재하는 경우에만 PascalCase로 파일명과 동일하게 작성

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

### 컴포넌트 구성
- 최하위 컴포넌트는 생성하지 않고, 부수 효과 없이 단일 태그만 사용
- 해당 태그의 스타일만 분리(.module.css)
- 컴포넌트 작성 규칙
```
import ... from '...';

function Foo () {
    return (
        <>
        </>
    );
}

export default Foo;
```
