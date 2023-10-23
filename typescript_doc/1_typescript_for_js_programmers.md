※ 모든 자료는 https://www.typescriptlang.org/ko/docs/ 에서 참고했습니다.※

[목차]<br/>

- []()<br/>

<br/>

# JavaScript Programmer를 위한 TypeScript

TypeScript는 JavaScript 위에 레이어로서 자리 잡고 있는데, JavaScript의 기능들을 제공하면서 그 위에 자체 레이어를 추가합니다. 이 레이어가 <b style="color: orange;">TypeScript 타입 시스템</b>입니다.

## 타입 추론 (Types by Inference)

TypeScript는 변수를 생성하면서 특정 값을 할당하는 경우, 그 값을 해당 변수의 타입으로 사용합니다.

## 타입 정의하기 (Defining Types)

자동으로 타입을 제공하기 힘들 때, 무엇이 되어야 하는지 명시 가능한 JavaScript 언어의 확장을 지원합니다.

```typescript
const user = {
  name: "Grog",
  id: 0,
};
```

이 객체의 형태를 명시적으로 나타내기 위해서는 `interface`로 선언합니다.

```typescript
interface User {
  name: string;
  id: number;
}
```

이제 변수 선언 뒤에 `:TypeName`의 구문을 사용해 <b>JavaScript 객체가 새로운 interface의 형태를 따르고 있음</b>을 선언할 수 있습니다.

```typescript
const user: User = {
  name: "Grog",
  id: 0,
};
```

해당 `interface`에 <b>맞지 않는 객체를 생성하면 경고</b>를 줍니다.

```typescript
//errors: 2322
const user: User = {
  username: "Grog",
  id: 0,
};
```

`interface`는 <b>Class</b>로도 선언할 수 있습니다.

```typescript
class UserAccount {
  name: string;
  id: number;

  constructor(name: string, id: number) {
    this.name = name;
    this.id = id;
  }

  user: User = new UserAccount("Grog", 0);
}
```

`interface`는 함수에서 <b>매개변수와 return 값을 명시</b>하는데 사용되기도 합니다.

```typescript
function getAdminUser(): User { ... }

function deleteUser(user: User) { ... }
```

JavaScript에서 사용할 수 있는 적은 종류의 원시 타입이 있습니다.
: boolean, bigint, null, number, string, symbol, object, undefined
TypeScript는 몇 가지 추가합니다.
:any(무엇이든 허용), unknown(이 타입을 사용하는 사람이 타입이 무엇인지 선언했는가를 확인), never(이 타입은 발생될 수 없음), void(undefined를 return하거나 return 값이 없는 함수), etc...

<br />

## 타입 구성 (Composing Types)

### 유니언 (Unions)

여러 타입 중 하나 일 수 있음을 선언하는 방법입니다.

```typescript
type MyBool = true | false;
```

유니턴 타입이 가장 많이 사용된 사례 중 하나는 값이 다음과 같이 허용되는 string 또는 number의 리터럴 집합을 설명하는 것입니다.

```typescript
type WindowStates = "open" | "closed" | "minimized";
type LockStates = "locked" | "unlocked";
type OddNumberUnderTen = 1 | 3 | 5 | 7 | 9;
```

### 제네릭 (Generics)

제네릭은 타입에 변수를 제공하는 방법입니다.
배열이 일반적인 예시이며, 제네릭이 없는 배열은 어떤 것이든 포함할 수 있습니다. 제네릭이 있는 배열은 배열 안의 값을 설명할 수 있습니다.

```typescript
type StringArray = Array<string>;
type NumberArray = Array<number>;
type ObejctWithNameArray = Array<{ name: string }>;
```

제네릭을 사용하는 고유 타입을 선언할 수 있습니다.

```typescript
//@error: 2345
interface Backpack<Type> {
  add: (obj: Type) => void;
  get: () => Type;
}

// 이 줄은 TypeScript에 'backpack'이라는 상수가 있음을 알리는 지름길이며
// const backpack: Backpack<string>이 어디서 왔는지 걱정할 필요가 없습니다.
declare const backpack: Backpack<string>;

// 위에서 Backpack의 변수 부분을 선언해서, object는 string입니다.
const object = backpack.get();

// backpack 변수가 string이므로, add 함수에 number를 전달할 수 없습니다.
backpack.add(23);
```

<br/>

## 구조적 타입 시스템 (Structural Type System)

TypeScript는 핵심 원칙 중 하나는 타입 검사가 값이 있는 형태에 집중한다는 것입니다. 이는 때때로 <b style="color: orange;">덕 타이핑(duck typing)</b> 또는 <b style="color: orange;">구조적 타이핑</b>이라고 불립니다.

구조적 타입 시스템에서 두 객체가 같은 형태를 가지면 같은 것으로 간주됩니다.

```typescript
interface Point {
  x: number;
  y: number;
}

function printPoint(p: Point) {
  console.log(`${p.x} ${p.y}`);
}

const point = { x: 12, y: 26 };
printPoint(point);
```

point 변수는 Point 타입으로 선언된 적이 없지만, TypeScript는 타입 검사에서 point의 형태와 Point의 형태를 비교합니다. 둘 다 같은 형태이기 때문에, 통과합니다.
