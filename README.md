# Clean Code

깨끗한 코드를 만들기 위해서는 고생을 해야 한다

## 1장. 깨끗한 코드

### **코드가 존재하리라**

프로그래밍이란 기계가 실행할 정도로 상세하게 요구사항을 명시하는 작업

고도로 추상화된 언어나 특정 응용 분야 언어로 기술하는 명세도 코드이므로 코드는 앞으로도 존재한다.

### **나쁜코드**

1. 나쁜코드는 개발 속도를 떨어뜨린다.
2. 나쁜코드가 쌓이면 팀 생산성이 떨어진다.
3. 0부터 시작하는 재설계는 시간이 엄청 오래 걸린다.
4. 좋은 코드를 사수하는 일은 프로그래머의 책임이다.

**기한을 맞추는 유일한 방법은 언제나 코드를 깨끗하게 유지하는 습관이다.**

### 깨끗한 코드란?

1. **비야네 스트롭스트룹 (C++ 창시자)**

- 보기에 즐거운 코드
- 의존성을 최소화 (유지보수가 쉬워짐)
- 세세한 사항까지 꼼꼼하게 오류 처리
- 한 가지에 집중

2. **그래디 부치**

- 가독성
- 명쾌한 추상화와 단순한 제어문

3. **데이브 토마스**

- 의미 있는 이름
- 다른 사람이 읽기 쉽고 고치기 쉬움
- 단위 테스트 케이스와 인수 테스트 케이스가 존재
- 의존성 , API 최소

4. **마이클 페더스**

- 주의 깊게 작성한 코드

5. **론 제프리스**

- 모든 테스트를 통과
- 중복이 없음
- 시스템 내 모든 설계 아이디어를 표현
- 클래스, 메서드, 함수 등을 최소화

6. **워드 커닝햄**

- 짐작했던 기능을 그대로 수행하는 코드

### **우리는 저자다**

새 코드를 짜면서 끊임없이 기존 코드를 읽는다. 그러므로 읽기 쉬운 코드는 중요하다.

1. **보이스카우트 규칙**

- 체크아웃할 때보다 좀 더 깨끗한 코드를 체크인
- 변수 이름 하나를 개선, 긴 함수 하나를 분할, 중복을 제거, 복잡한 if문 하나 정리

1. **프리퀄과 원칙**

객체 지향 설계의 원칙

- SRP(Single Responsibility Principle): 클래스에는 한 가지, 단 한 가지 변경 이유만 존재해야 한다.
- OCP(The Open Closed Principle): 클래스는 확장에 열려 있어야 하며 변경에 닫혀 있어야 한다.
- LSP(The Liskov Substitution Principle): 상속받은 클래스는 기초 클래스를 대체할 수 있어야 한다.
- DIP(The Dependency Inversion Principle): 추상화에 의존해야 하며, 구체화에 의존하면 안 된다.
- ISP(The Interface Segregation Principle): 클라이언트에 밀접하게 작게 쪼개진 인터페이스를 유지한다.

## 2장. 의미있는 이름

### 의도를 분명히 밝혀라

해당 질문에 답해야 한다

- 변수의 존재 이유는? 수행 기능은? 사용 방법은?

```jsx
//<나쁜 코드>
public List<int[]> getThem(){
	List<int[]> list1 = new ArrayList<int[]>();
	for (int[] x : theList)
		if (x[0] == 4)
			list1.add(x);
	return list1;
}

//<좋은 코드>
public List<Cell> getFlaggedCells() {
	List<Cell> flaggedCells = new ArrayList<Cell>();
	for (Cell cell : gameBoard)
		if (cell.isFlagged())
			flaggedCells.add(cell);
		return flaggedCells;
}
```

### 그릇된 정보를 피하라

1. 의미가 있는 단어를 다른 의미로 사용하면 안된다
2. 흡사한 이름을 사용하지 않도록 주의한다
3. 유사한 개념은 유사한 표기법을 사용한다
4. 일관성이 떨어지는 표기법은 그릇된 정보다

### 의미 있게 구분하라

연속된 숫자를 덧붙이거나 불용어를 추가하는 방식은 적절하지 않다.

불용어는 중복이다

읽는 사람이 차이를 알도록 이름을 지어야 한다.

- moneyAmount, money와 customerInfo, customer와 accountData, account와 theMessage와 message는 구분이 안 된다.

```jsx
// 나쁜함수
getActiveAccount();
getActiveAccounts();
getActiveAccountInfo();
```

### 발음하기 쉬운 이름을 사용하라

검색하기 쉬운 이름을 사용하라

- 함수명이 길어도 이름을 의미있게 지어야 검색이 쉽다

### 인코딩을 피하라

인터페이스 클래스와 구현 클래스

- 구현 클래스 이름이 더 직관적이다
- 접두어 사용 지양

### 자신의 기억력을 자랑하지 마라

- 명료함이 최고

### 클래스 이름

- 명사나 명사구가 적합
- 좋은 예) Customer, WikiPage, Account, AddressParser
- 나쁜 예) Manager, Processor, Data, Info
- 동사 사용X

### 매서드 이름

- 동사나 동사구가 적합
- 좋은 예) postPayment, deletePage, save
- 접근자, 변경자, 조건자는 javabean 표준에 따라 앞에 get, set, is를 붙인다
- 생성자를 중복정의할 때는 정적 팩토리 메서드를 사용한다

### 기발한 이름은 피하라

### 한 개념에 한 단어를 사용하라

- 메서드 이름은 독자적이고 일관적이어야 한다

### 해법 영역에서 가져온 이름을 사용하라

### 문제 영역에서 가져온 이름을 사용하라

### 의미 있는 맥락을 추가하라

```jsx
//맥락이 분명한 변수
public class GuessStatisticsMessage {
	private String number;
	private String verb;
	private String pluralModifier;

	public String make(char candidate, int count) {
		createPluralDependentMessageParts(count);
		return String.format(
			"There %s %s %s%s",
				verb, number, candidate, pluralModifier );
	}

	private void createPluralDependentMessageParts(int count) {
		if (count == 0) {
			thereAreNoLetters();
		} else if (count == 1) {
			thereIsOneLetter();
		} else {
			thereAreManyLetters(count);
		}
	}
}
```

### 불필요한 맥락을 없애라

- accountAddress와 customerAddress는 Address 클래스 인스턴스로는 좋은 이름이나 클래스 이름으로는 적합하지 못하다. Address는 클래스 이름으로 적합하다

## 3장. 함수

함수를 만드는 규칙!

### 작게 만들어라

- 함수를 짧게 만들자
- 함수의 들여쓰기 수준은 1단이나 2단을 넘어서면 안 된다
- if문 /else 문/while 문 등에 들어가는 블록은 한 줄이어야 한다

```jsx
public static String renderPageWithSetupsAndTeardowns(
	PageDate pageData, boolean isSuite) throws Exception {
	if (isTestPage(pageData))
		includeSetupAndTeardownPages(pageData, isSuite);
	return pageData.getHtml();
}
```

### 한 가지만 해라!

1. 페이지가 테스트 페이지인지 판단한다
2. 그렇다면 설정 페이지와 해제 페이지를 넣는다
3. 페이지를 HTML로 렌더링한다

**TO 문단으로 기술**

> TO RenderPageWithSetupsAndTeardowns, 페이지가 테스트 페이지인지 확인한 후 테스트 페이지라면 설정 페이지와 해제 페이지를 넣는다. 테스트 페이지든 아니든 페이지를 HTML로 렌더링한다.

세 단계는 지정된 함수 이름 아래에서 추상화 수준이 하나다

지정된 함수 이름 아래에서 추상화 수준이 하나인 단계만 수행한다면 그 함수는 한 가지 작업만 한다.

함수가 ‘한 가지’만 하는지 판단하는 방법

- 단순히 다른 표현이 아니라 의미 있는 이름으로 다른 함수를 추출할 수 있다면 그 함수는 여러 작업을 하는 셈이다.

함수 당 추상화 수준은 하나로

위에서 아래로 코드 읽기: 내려가기 규칙

- 코드는 위에서 아래로 이야기처럼 읽혀야 좋다
- 함수 추상화 수준이 한 번에 한 단계씩 낮아진다

### switch 문

- switch는 추상 팩토리에 숨긴다

### 서술적인 이름을 사용하라!

- testableHtml → SetupTeardownIncluder.render로 변경
- 길어도 쉽게 의도를 파악할 수 있는 이름이 좋다

### **함수 인수**

- 최선은 입력 인수가 없는 경우이며, 차선은 입력 인수가 1개뿐인 경우다

### 부수 효과를 일으키지 마라!

- 시간적인 결합이나 순서 종속성을 초래
- 출력 인수는 피해야 한다. 함수에서 상태를 변경해야 한다면 함수가 속한 객체 상태를 변경하는 방식을 택한다.

### 명령과 조회를 분리하라!

```jsx
<나쁜 코드>
if (set("username", "unclebob"))

<좋은 코드>
if (attributeExists("username")) {
	setAttribute("username", "unclebob");
	...
}
```

### 오류 코드보다 예외를 사용하라!

- try/catch 블록 뽑아내기

### 반복하지 마라!

- 중복 제거

구조적 프로그래밍

- 모든 함수와 함수 내 모든 블록에 입구와 출구가 하나만 존재해야 한다. 즉, 함수는 return 문이 하나여야 한다. 루프 안에서 break나 continue를 사용해선 안 되며 goto는 절대로 안된다.

### 결론

모든 시스템은 특정 응용 분야 시스템을 기술할 목적으로 프로그래머가 설계한 도메인 특화 언어로 만들어진다. 함수는 그 언어에서 동사며, 클래스는 명사다.

앞서 말한 규칙을 따라 함수를 작성해 시스템을 기술하도록 하자.
