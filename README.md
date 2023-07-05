# msw를 Next.js 13에서 사용하는 방법

## 해결 방법

- 간단히 버전만 맞춰주면 됩니다. 가능한 최신 버전의 조합은 아래와 같습니다:
- Node.js 16.20.1 (LTS) (`nvm use 16`)
- Next.js 13.3.4 (23/05/01 릴리즈)
- msw 1.2.2 (23/06/10 릴리즈)

## 문제점

### 1. [Example Repo](https://github.com/vercel/next.js/tree/canary/examples/with-msw)가 미동작

- 원인: Next.js의 최신 버전 + Node.js 버전 제한이 없는 점

### 2. msw는 Node v18 미지원

- `msw`는 현재 Node v18을 미지원
- `msw@next`는 Node v18을 지원하지만, Next.js와 사용 시 TypeError 발생.

### 3. Next.js 13.4.0 + msw 사용 시 두 번째 요청부터 TypeError 발생

## 예상 원인 범위

- Next.js의 `13.3.4` -> `13.4.0` 사이에 문제의 원인이 있을 것으로 보임.
- `13.3.4`와 `13.4.0` 사이에는 109 Commit, 584 Files changed가 있음.
- [Next.js Releases](https://github.com/vercel/next.js/releases) 참고
- `13.4.0`이 5월 5일 출시 - 오류 발생
- `13.3.5`는 미출시되고 바로 `13.4.0`으로 버전 업.
- `13.3.4`가 5월 1일 출시 - 정상 동작
- `13.3.2`가 4월 30일 출시 - 정상 동작
- `13.3.1`이 4월 22일 출시 - 정상 동작
- `13.3.0`이 4월 7일 출시 - 정상 동작
