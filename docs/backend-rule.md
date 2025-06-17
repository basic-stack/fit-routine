# Backend 규칙

## 코딩 컨벤션

코드를 작성할 땐 [캠퍼스 핵데이 Java 코딩 컨벤션](https://naver.github.io/hackday-conventions-java/)을 따라야 합니다.

## Null 처리 규칙

반환 타입, 필드 타입, 파라미터 타입 등 코드 상에 존재하는 모든 타입은 `null` 일 가능성이 있다면, 반드시 `@Nullable` 어노테이션을 붙여야 합니다. 해당 어노테이션은
`org.springframework.lang` 에 위치합니다.

예시는 다음과 같습니다:

```java
import org.springframework.lang.Nullable;

public final class Container {
    private @Nullable Foo foo;

    public void setFoo(@Nullable Foo foo) {
        this.foo = foo;
    }

    public @Nullable Foo getFoo() {
        return foo;
    }
}
```

단, 이 어노테이션은 항상 타입 앞에 붙여야 합니다. 메서드 앞에 붙이지 마세요:

```java
// 올바른 사용
public @Nullable Foo getFoo() {
	return foo;
}

// 잘못된 사용
@Nullable
public Foo getFoo() {
	return foo;
}
```

## REST API 설계 규칙 준수

REST API 설계 규칙을 따라야 합니다.

### 리소스 명명 규칙

- **URL은 명사**로 작성 (동사 사용 금지)
- 계층 관계는 `/상위리소스/{id}/하위리소스` 형식

```
# 예시
GET /users                # 사용자 목록 조회
GET /users/{userId}       # 특정 사용자 조회
GET /users/{userId}/posts # 사용자의 게시글 조회
```

### Controller 전달 값 규칙

- 전달 값이 하나인 경우(PK) : @PathVariable
- 객체 또는 예민한 정보 : @RequestBody

### HTTP 메서드 사용 규칙

| 메서드      | 역할            | 예시                      |
|----------|---------------|-------------------------|
| `GET`    | 리소스 **조회**    | `GET /products`         |
| `POST`   | 리소스 **생성**    | `POST /products`        |
| `PUT`    | 리소스 **전체 수정** | `PUT /products/{id}`    |
| `PATCH`  | 리소스 **부분 수정** | `PATCH /products/{id}`  |
| `DELETE` | 리소스 **삭제**    | `DELETE /products/{id}` |

### 응답 상태 코드 규칙

| 코드    | 의미                    | 사용 시나리오         |
|-------|-----------------------|-----------------|
| `200` | OK (요청 성공)            | 조회 성공 시         |
| `201` | Created (생성 완료)       | `POST` 성공 시     |
| `204` | No Content (삭제 완료)    | `DELETE` 성공 시   |
| `400` | Bad Request (잘못된 요청)  | 파라미터 오류         |
| `404` | Not Found (리소스 없음)    | 존재하지 않는 ID 접근 시 |
| `500` | Internal Server Error | 서버 내부 오류        |

### 데이터 처리 규칙

- **필터링/정렬**: 쿼리 파라미터 사용
  ```http
  GET /users?role=admin&sort=-created_at
  ```
- **페이징**: `size`, `page` 사용
  ```http
  GET /posts?page=2&size=10
  ```

## Lombok 스타일

### Annotation 규칙

명시적 선언과 안정성을 위해 `@AllArgsConstructor`, `@RequiredArgsConstructor`, `@Data` 사용을 지양합니다. `@Getter`와 `@Setter`를 사용하고,
`private` 생성자에 `@Builder`를 사용하는 패턴을 기본으로 하세요.

예시는 다음과 같습니다:

```java
@Getter
class Person {
    private final String name;
    private final int age;
    private final int code;

    // 여기서 중요한 점은, `private`로 선언하여 빌더로만 생성할 수 있도록 하는 것입니다.
    @Builder
    private Person(String name, int age, int code) {
        this.name = name;
        this.age = age;
        this.code = code;
    }
}

// 각 값이 무엇을 의미하는지 단번에 파악할 수 있음.
Person person = Person.builder()
        .name("홍길동")
        .age(30)
        .code(82)
        .build();
```

다음 글을 참고하세요.

- [Why you should not use Lombok](https://ppbruna.medium.com/why-you-should-not-use-lombok-f7556662e8c3)
- [Lombok 사용상 주의점](https://kwonnam.pe.kr/wiki/java/lombok/pitfall)

### DTO, VO 외 사용 지양

부수 효과를 방지하기 위해 **DTO**, **VO** 외 사용을 지양합니다. 대신 직접 작성하도록 합니다.
<br/>
DTO 접미사 없이 작성 (ProfileInfoDTO - X, ProfileInfo - O)
VO는 DB의 테이블명과 동일하게 작성 (TB_MEMBER인 경우 MEMBER)

예시는 다음과 같습니다:

```java
// 나쁜 사용
@Service
@RequiredArgsConstructor
public final class MemberService {
    private final MemberMapper memberMapper;
}

// 바른 사용
@Service
public final class MemberService {
    private final MemberMapper memberMapper;

    public MemberService(MemberMapper memberMapper) {
        this.memberMapper = memberMapper;
    }
}
```

## Mybatis 스타일

**인터페이스**와 **XML 기반 매핑**을 사용합니다. **클래스**와 **Annotation 기반 매핑**은 사용하지 않습니다.

## 기타 권고 사항

다음 내용은 권고 사항으로, 반드시 지켜야 하는 것은 아닙니다.

### final 기본 사용

- 모든 클래스/메서드/필드는 기본적으로 `final`로 선언한다.
- 필요한 경우에만 `non-final`로 변경한다.
- 예외: 파라미터, 로컬 변수에는 `final`이 큰 의미가 없다.

### 불변성 우선

- **DTO**, **VO** 등의 데이터를 표현하는 객체는 기본적으로 불변으로 설계한다.
- 필요한 경우, 필요한 부분만 가변으로 전환한다.
- `Lombok`을 사용하는 경우, 필드를 `final`로 선언하면 불변이다.
