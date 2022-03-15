## 클릭 아키텍처 : 소프트웨어 구조와 설계의 원칙
* 책을 읽고, 인상적인 구절을 남긴다.

---
## 4장 구조적 프로그래밍
p.35 : 테스트
> 프로그램이 잘못되었음을 테스트를 통해 증명할 수는 있지만, 프로그램이 맞다고 증명할 수 없다.   
> 테스트에 충분한 노력을 들였다면, 테스트가 보장할 수 있는 것은 프로그램이 목표에 부합할 만큼은 충분히 참이라고 여길 수 있게 해주는 것이 전부다.

---
## 5장 객체 지향 프로그래밍
p.38 ~ p.51 : 캡슐화/상속/다형성
* 객체지향은 캡슐화를 강제하지 않음.
* 객체지향만 캡슐화를 할 수 있는 것이 아님.
* 객체지향이 아니더라도 충분히 타 언어에서 상속 흉내가 가능.
* 객체지향에서는 상속을 편하게 하도록 기능을 제공.
* 다형성을 통해, 고수준모듈과 저수준모듈의 독립성을 보장받을 수 있음.

---
## 6장 함수형 프로그래밍
p.58 : 불변성과 아키텍처
* 아키텍처를 고려할 때, 변수의 가변성을 고려해야 한다.
  * 아래의 문제가 모두 가변변수로 인해서 발생한다.
    * 경합조건 (race condition)
    * 교착상태 (deadlock)
    * 동시 업데이트 (concurrent update)
* 아키텍트라면 동시성 문제에 관심을 가져야 한다.

---
## 7장 SRP : 단일 책임 원칙
* SRP 는 모듈은 반드시 하나의, 단 하나의 일만 해야한다 (X)
  * `잘못된 이해를 하고 있었음.` -> 원래는 함수가 단 하나의 일만 해야한다는 원칙임
* SRP 는 단일 모듈의 변경의 이유가 오직 하나뿐이어야 한다. (O)
  * 변경의 이유란?, 사용자와 이해관계자를 가리킨다.
    * 한 명의 사용자 혹은 한 명 이상의 특정한 이해관계자에 대해서만 책임을 가진다.
  * 하나의 모듈은 하나의, 오직 하나의 액터에 대해서만 책임을 가져야 한다.
  * 액터(actor) 란?, 한 명 이상의 특정한 집단을 가리킨다.
* 서로 다른 액터를 뒷받침 하는 코드를 서로 분리하는 것.

> 문득, 실무가 생각난다.   
> DDD 의 계층형 아키텍처를 고려하면 결국 아래와 같은 순으로 하는게 좋지 않을까?   
> controller -> application service -> interactor -> infra/repository

---
## 8장 OCP : 개방-폐쇄 원칙
* 소프트웨어 개체의 행위는 확장할 수 있어야 하지만, 이 때 개체를 변경해서는 안된다.
* `추이종속성 (transitive dependency)` 을 가지면 안된다.
  * 클래스 A 가 클래스 B 에 의존한다.
  * 클래스 B 가 클래스 C 에 의존한다.
  * 결과적으로 클래스 A 가 클래스 C 에 의존한다.

---
## 9장 LSP : 리스코프 치환 원칙
p.82 ~ p.86 
* 책을 한번 더 짧게 읽자.

---
## 10장 ISP : 인터페이스 분리 원칙
* 책을 한번 더 짧게 읽자.
* 필요 이상으로 많은 걸 포함하는 모듈에 의존하는 것은 해로운 일이다.
* 소스 코드 의존성의 경우 이는 분명한 사실인데, 불필요한 재컴파일과 재배포를 강제하기 때문이다.

---
## 11장 DTP : 의존성 역전 원칙
* 정적 타입 언어에서 오직 인터페이스나 추상 클래스 같은 추상적인 선언만을 참조해야 한다.
  * 구체적인 대상에는 절대로 의존해서는 안된다.

안정화된 추상화
* 변동성이 큰 구체 클래스를 참조하지 말라
  * 대신 추상 인터페이스를 참조하라
* 변동성이 큰 구체 클래스로부터 파생하지 말라
  * 상속은 신중하게.
  * 정적 타입 언어에서 상속은 소스 코드에 존재하는 모든 관계 중 가장 강력한 동시에 뻣뻣해서 변경하기 어렵다.
    * `해당 내용을 읽다보니, 상속에 관해 쓴 과거 블로그 글이 떠오름` : [링크](https://pasudo123.tistory.com/446)

팩토리
* 소스 코드 의존성은 제어흐름과 반대 방향으로 역전된다. 이러한 이유로 이 원칙을 의존성 역전이라고 부른다.
