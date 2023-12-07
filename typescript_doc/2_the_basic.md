※ 모든 자료는 https://www.typescriptlang.org/ko/docs/ 에서 참고했습니다.※

[목차]<br/>

- []() <br/>

<br/>

# The Basic

<b style="color: orange;">정적 타입 시스템</b>은 우리가 작성한 프로그램에서 사용된 값들의 형태와 동작을 설명합니다. TypeScript와 같은 타입 검사기는 이 정보를 활용하여 프로그램이 제대로 작동하지 않을 때 알려줍니다.

```typescript
const message = "hello!";

message();
// This expression is not callable.
// Type 'String' has no call signatures.
```

코드가 실행되기에 앞서 우선 오류 메시지를 확인하게 됩니다.

<br/>

## 예외가 아닌 실행 실패

TypeScript는 겉으로 드러나지 않는 버그를 꽤 많이 잡아냅니다.

```typescript
function flipCoin() {
  return Math.random < 0.5;
  // Operator '<>' cannot be applied to types '() => number' and 'number'.
}
```

<br/>

## 프로그래밍 도구로서의 타입

TypeScript는 프로그래밍 도구를 중요하게 생각하며, 여기에는 코드 완성 및 오류 메시지 기능 이외에도 다양한 것이 포함됩니다. TypeScript를 지원하는 코드 편집기는 <b>오류를 자동으로 고쳐주는 "Quick Fixes", 코드를 간편하게 재조직하는 리팩토링, 변수의 정의로 빠르게 이동하는 유용한 네비게이션, 주어진 변수에 대한 모든 참조 검색</b> 등의 기능들을 제공합니다.

<br/>

## tsx, TypeScript compiler

npm을 사용하여 설치하도록 하겠습니다.

```
npm install -g typescript
```

빈 폴더로 이동하여 첫 번째 TypeScript 프로그램인 hello.ts를 작성해보도록 하겠습니다.

```typescript
console.log("Hello World!");
```

typescript 패키지와 함께 설치된 `tsc` 명령어를 실행하여 타입 검사를 수행합니다.

```
// 글로벌
tsc hello.ts

// 로컬
npx tsc hello.ts
```

우리는 파일 출력을 얻었습니다. 현재 디렉토리를 보면, hello.js 파일이 있는 것을 볼 수 있습니다. 이것이 tsc가 우리의 hello.ts 파일을 JavaScript 파일로 컴파일 또는 변형한 결과물입니다.

만약 타입 겸사 오류가 주어지면 어떨까요?

```typescript
function greet(person, data) {
  console.log(`Hello ${person}, today is ${date}!`);
}

greet("Brendan");
```

여기서 `tsc hello.ts`를 다시 실행하면, 커맨드 라인 상에서 오류를 얻게 됩니다.

```
Expected 2 arguments, but got 1.
```

### 오류 발생시키기

hello.js 파일의 내용이 또 한 번 수정되었습니다. 파일을 열어보면, 입력으로 사용된 코드 파일과 실질적으로 동일하다는 것을 알 수 있습니다. 우리 코드를 보고 `tsc`가 오류를 발생시켰다는 점을 감안하면 다소 놀랍게 느껴질 수도 있지만, 이는 TypeScript의 핵심 가치 중 하나에 기반한 동작입니다.

앞에서도 말씀드렸듯이 코드에 대한 타입 검사는 프로그램이 실행할 수 있는 동작을 제한합니다. 따라서 타입 검사가 허용 또는 제한하는 동작의 범위에는 어느 정도 절충과 타협이 존재합니다. 대부분의 경우 문제가 발생하지 않지만, 타입 검사가 방해가 되는 시나리오 또한 존재합니다. 예를 들어, JavaScript로 작성된 코드를 TypeScript로 마이그레이션하는 과정에서 타입 검사 오류가 발생하는 경우를 떠올려보세요. 결국에는 타입 검사를 통과하도록 코드를 수정해나가겠지만, 사실 원본 JavaScript 코드는 이미 제대로 잘 작동하고 있는 상태였습니다. TypeScript로 변환하는 작업 때문에 코드 실행이 중단되어야 할 이유가 있을까요?

그래서 TypeScript는 당신을 방해하지 않습니다. 물론, 시간이 흐름에 따라 좀 더 실수에 방어적으로 대응하고, TypeScript가 보다 엄격하게 동작하기를 원할 수도 있습니다. 이 경우 `--noEmitOnError` 컴파일 옵션을 사용하면 됩니다. hello.ts 파일을 수정한 뒤 위 플래그 옵션을 사용하여 `tsc`를 실행해보세요.

```
tsc --noEmitOnError hello.ts
```

hello.js가 하나도 수정되지 않는다는 것을 확인할 수 있습니다.
