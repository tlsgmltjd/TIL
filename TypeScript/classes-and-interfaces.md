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

- **추상 메서드** (추상 클래스 안의 메서드)  
  추상 메서드는 **추상 클래스를 상속받는 클래스들이 반드시 구현(implement)해야하는 메서드**이다.

```
📌접근 가능한 위치

구분　　　 선언한 클래스 내　상속받은 클래스 내　인스턴스
private 　 　　　 ⭕ 　　　　　　　 ❌ 　　　　　 ❌
protected 　　　 ⭕ 　　　　　　　 ⭕ 　　　　　 ❌
public 　　　　　 ⭕ 　　　　　　　 ⭕ 　　　　　 ⭕
```
