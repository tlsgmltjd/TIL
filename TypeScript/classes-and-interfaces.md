## Classes

```ts
abstract class User {
  constructor(
    protected firstName: string,
    protected lastName: string,
    protected nickName: string
  ) {}

  // 추상 메서드
  // 추상 메서드는 추상 클래스를 상속받는 클래스들이 반드시 구현(implement)해야하는 메서드이다.
  abstract getNickName(): void;

  public getFullName() {
    return `${this.firstName} ${this.lastName} ${this.nickName}`;
  }
}

class Player extends User {
  getNickName() {
    console.log(this.nickName);
  }
}

const user1 = new Player("Lee", "jinheon", "robo");

user1.getFullName();
user1.getNickName();
```

- **추상(abstract) 클래스**
  **추상 클래스는 오직 다른 클래스가 상속받을 수 있는 클래스**이다.
  하지만 **직접 새로운 인스턴스를 만들 수는 없다.**

- **추상 메서드** (추상 클래스 안의 abstract 키워드를 붙힌 메서드)  
  추상 메서드는 **추상 클래스를 상속받는 클래스들이 반드시 구현(implement)해야하는 메서드**이다.

```
📌접근 가능한 위치

구분　　　 선언한 클래스 내　상속받은 클래스 내　인스턴스
private 　 　　　 ⭕ 　　　　　　　 ❌ 　　　　　 ❌
protected 　　　 ⭕ 　　　　　　　 ⭕ 　　　　　 ❌
public 　　　　　 ⭕ 　　　　　　　 ⭕ 　　　　　 ⭕
```

<br />

```ts
type Words = {
  [key: string]: string;
};

class Dict {
  private words: Words;

  constructor() {
    this.words = {};
  }

  // 단어 추가 메서드
  add(word: Word) {
    if (this.words[word.term] === undefined) {
      this.words[word.term] = word.def;
    }
  }

  // 단어 삭제 메서드
  del(term: string) {
    if (!(this.words[term] == undefined)) {
      delete this.words[term];
    }
  }

  // 모든 단어 출력 메서드
  all() {
    for (let i in this.words) {
      console.log(`${i} : ${this.words[i]}`);
    }
  }

  // 단어 찾아서 반환 메서드
  def(term: string) {
    return this.words[term];
  }
}

class Word {
  constructor(public term: string, public def: string) {}
}

const kimchi = new Word("김치", "한국의 음식");
const rice = new Word("밥", "한국의 음식");
const pizza = new Word("피자", "한국의 음식이 아님");

const dict = new Dict();

dict.add(kimchi);
dict.add(rice);
dict.add(pizza);

dict.del("김치");

dict.all();
// [LOG]: "밥 : 한국의 음식"
// [LOG]: "피자 : 한국의 음식이 아님"
```

## Interfaces

- 오브젝트나 클래스의 타입을 특정해주기 위해 사용한다.

```ts
interface Person {
  name: string;
}

// 똑같다
/*
type Person = {
  name: string;
};
*/

const user1: Person = {
  name: "jinheon",
};
```

- interface는 상속의 개념을 사용할 수 있다.

```ts
interface User {
  name: string;
}

interface Player extends User {
  age: number;
}

const user1: Player = {
  name: "jinheon", // 상속 받은 속성 사용가능
  age: 17,
};
```

---

```ts
// 추상 클래스는 그 자신만으로 인스턴스를 만들 수 없다.
// 상속 받는 클래스가 어떻게 동작해야할 지 알려주기 위해 사용한다.
// 추상 클래스로 만들면 JS로 변환될 때 일반 클래스로 변환된다.
abstract class User {
  constructor(protected firstName: string, protected lastName: string) {}

  abstract sayHi(name: string): string;
  abstract fullName(): string;
}

class Player extends User {
  fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
  sayHi(name: string) {
    return `Hello ${name}! My name is ${this.fullName()}`;
  }
}
```

### implements

- `implements`을 사용하여 `클래스`가 `특정 인터페이스를 충족하는지` 확인할 수 있다.

> interface와 implements를 사용하여 표현

```ts
interface User {
  firstName: string;
  lastName: string;
  sayHi(name: string): string;
  fullName(): string;
}

interface Human {
  health: number;
}

class Player implements User, Human {
  constructor(
    public firstName: string,
    public lastName: string,
    public health: number
  ) {}
  fullName() {
    return `${this.firstName} ${this.lastName}`;
  }
  sayHi(name: string) {
    return `Hello ${name}! My name is ${this.fullName()}`;
  }
}
```

---

- `interface` vs `type`

```ts
type PlayerA = {
  name: string;
};

type PlayerAA = PlayerA & {
  lastName: string;
};

const playerA: PlayerAA = {
  name: "jinheon",
  lastName: "xxx",
};

/////

interface PlayerB {
  name: string;
}

interface PlayerB {
  lastName: string;
}

interface PlayerB {
  health: number;
}

const playerB: PlayerB = {
  name: "jinheon",
  lastName: "xxx",
  health: 10,
};
```

---

- interface 끼리 상속은 extends를 사용하며 class 상속은 implements를 사용
