# Coding Convention

> 2021년 7월 30일 - Project Review

## 코드 품질

- 코드가 하고자 하는 행위를 효율적으로 할 수 있는지 등 여러 기준으로 평가
- 한가지 기준만으로 평가할 수 없음

## 코딩 규칙 (Coding Convention)

- 해당 언어로 작성된 프로그램의 각 측면에 대한 **프로그래밍 스타일, 관행 및 방법**을 권장하는 특정 프로그래밍 언어에 대한 일련의 지침
- 소프트웨어 프로그래머는 **소스 코드의 가독성을 개선**하고 소프트웨어 **유지보수를 용이**하게 하기 위해 이런 지침을 따르는 것이 좋음
- 협약은 전체 팀 또는 회사가 따라야 하는 문서화된 규칙 집합으로 **공식화** 될 수도 있고 개인의 습관적인 코딩 관행처럼 **비공식적** 일 수도 있고, 컴파일러에 의해 시행되는 것이 아님

## 코딩 컨벤션 세부 항목

- 파일 구성 (file organization)
- 들여쓰기 (indention)
- 주석 (comments)
- 선언 (declarations)
- 명령문 (statements)
- 공백 (white space)
- 명명규칙 (naming convention)
- 프로그래밍 관행 (programming practices)
- 프로그래밍 원칙 (programming principles)
- 아키텍처 모범 사례

### Case Types

- SNEKE_CASE (UPPER_SNAKE)
- snake_case (lower_snake)
- camelCase
- UpperCamel (PascalCase)
- kebab-case

### 들여쓰기 (Indent)

- Spaces vs Tabs
- 몇 칸 띄어쓸지 (2, 3, 4칸...)

### 중괄호 (Brace)

- 옆 vs 및

## Coding Convention 예시

- [Java Code Convention - Oracle](https://www.oracle.com/technetwork/java/codeconventions-150003.pdf)
- [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
- [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)
- [Google TypeScript Style Guide](https://google.github.io/styleguide/tsguide.html)
- [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
- [Airbnb React/JSX Style Guide](https://github.com/airbnb/javascript/tree/master/react)
- [Apple Objective-C Conventions](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Conventions/Conventions.html)
- [PEP 8 - Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/)
- [Kotlin Coding Convention](https://kotlinlang.org/docs/coding-conventions.html)
- [Swift Style Guide](https://google.github.io/swift/)
- [코딩 컨벤션 | TOAST UI](https://ui.toast.com/fe-guide/ko_CODING-CONVENTION)
- [NHN 코딩 컨벤션](https://nuli.navercorp.com/data/convention/NHN_Coding_Conventions_for_Markup_Languages.pdf)
- [Naver JavaScript Coding Conventions](https://github.com/naver/eslint-config-naver)

### Coding Convention 결정이 어렵다면

- Google Style Guides를 쓰자

## Google Java Coding Convention

> [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)

### 2.1 File name

- The source file name consists of the case-sensitive name of the top-level class it contains (of which there is [exactly one](https://google.github.io/styleguide/javaguide.html#s3.4.1-one-top-level-class)), plus the `.java` extension.

### 2.2 File encoding: UTF-8

- Source files are encoded in **UTF-8**.

### 2.3.1 Whitespace characters

- Aside from the line terminator sequence, the **ASCII horizontal space character** (**0x20**) is the only whitespace character that appears anywhere in a source file. This implies that:
  1. All other whitespace characters in string and character literals are escaped.
  2. Tab characters are **not** used for indentation.

### 3.3.1 No wildcard imports

- **Wildcard imports**, static or otherwise, **are not used**.

### 4.1.1 Braces are used where optional

- Braces are used with `if`, `else`, `for`, `do` and `while` statements, even when the body is empty or contains only a single statement.

### 4.1.2 Nonempty blocks: K & R style

- Braces follow the Kernighan and Ritchie style ("[Egyptian brackets](http://www.codinghorror.com/blog/2012/07/new-programming-jargon.html)") for *nonempty* blocks and block-like constructs:

  - No line break before the opening brace.
  - Line break after the opening brace.
  - Line break before the closing brace.
  - Line break after the closing brace, *only if* that brace terminates a statement or terminates the body of a method, constructor, or *named* class. For example, there is *no* line break after the brace if it is followed by `else` or a comma.

- Examples:

  ```java
  return () -> {
    while (condition()) {
      method();
    }
  };
  
  return new MyClass() {
    @Override public void method() {
      if (condition()) {
        try {
          something();
        } catch (ProblemException e) {
          recover();
        }
      } else if (otherCondition()) {
        somethingElse();
      } else {
        lastThing();
      }
    }
  };
  ```

### 4.1.3 Empty blocks: may be concise

- An empty block or block-like construct may be in K & R style (as described in [Section 4.1.2](https://google.github.io/styleguide/javaguide.html#s4.1.2-blocks-k-r-style)). Alternatively, it may be closed immediately after it is opened, with no characters or line break in between (`{}`), **unless** it is part of a multi-block statement (one that directly contains multiple blocks: `if/else` or `try/catch/finally`).

- Examples:

  ```java
  // This is acceptable
  void doNothing() {}
  
  // This is equally acceptable
  void doNothingElse() {
  }
  ```

  ```java
  // This is not acceptable: No concise empty blocks in a multi-block statement
  try {
    doSomething();
  } catch (Exception e) {}
  ```

### 4.2 Block indentation: +2 spaces

- Each time a new block or block-like construct is opened, the indent increases by two spaces. When the block ends, the indent returns to the previous indent level. The indent level applies to both code and comments throughout the block. (See the example in Section 4.1.2, [Nonempty blocks: K & R Style](https://google.github.io/styleguide/javaguide.html#s4.1.2-blocks-k-r-style).)

### 4.4 Column limit: 100

- Java code has a column limit of 100 characters. A "character" means any Unicode code point. Except as noted below, any line that would exceed this limit must be line-wrapped, as explained in Section 4.5, [Line-wrapping](https://google.github.io/styleguide/javaguide.html#s4.5-line-wrapping).

> Each Unicode code point counts as one character, even if its display width is greater or less. For example, if using [fullwidth characters](https://en.wikipedia.org/wiki/Halfwidth_and_fullwidth_forms), you may choose to wrap the line earlier than where this rule strictly requires.

- Exceptions:
  1. Lines where obeying the column limit is not possible (for example, a long URL in Javadoc, or a long JSNI method reference).
  2. `package` and `import` statements (see Sections 3.2 [Package statement](https://google.github.io/styleguide/javaguide.html#s3.2-package-statement) and 3.3 [Import statements](https://google.github.io/styleguide/javaguide.html#s3.3-import-statements)).
  3. Command lines in a comment that may be cut-and-pasted into a shell.

### 4.6.2 Horizontal whitespace

- Beyond where required by the language or other style rules, and apart from literals, comments and Javadoc, a single ASCII space also appears in the following places **only**.

  1. Separating any reserved word, such as `if`, `for` or `catch`, from an open parenthesis (`(`) that follows it on that line

  2. Separating any reserved word, such as `else` or `catch`, from a closing curly brace (`}`) that precedes it on that line

  3. Before any open curly brace (`{`), with two exceptions:

     - `@SomeAnnotation({a, b})` (no space is used)
     - `String[][] x = {{"foo"}};` (no space is required between `{{`, by item 8 below)

  4. On both sides of any binary or ternary operator. This also applies to the following "operator-like" symbols:but not

     - the ampersand in a conjunctive type bound: `<T extends Foo & Bar>`
     - the pipe for a catch block that handles multiple exceptions: `catch (FooException | BarException e)`
     - the colon (`:`) in an enhanced `for` ("foreach") statement
     - the arrow in a lambda expression: `(String str) -> str.length()`
     - the two colons (`::`) of a method reference, which is written like `Object::toString`
     - the dot separator (`.`), which is written like `object.toString()`

  5. After `,:;` or the closing parenthesis (`)`) of a cast

  6. On both sides of the double slash (`//`) that begins an end-of-line comment. Here, multiple spaces are allowed, but not required.

  7. Between the type and variable of a declaration: `List<String> list`

  8. Optional

      just inside both braces of an array initializer

     - `new int[] {5, 6}` and `new int[] { 5, 6 }` are both valid

  9. Between a type annotation and `[]` or `...`.

- This rule is never interpreted as requiring or forbidding additional space at the start or end of a line; it addresses only *interior* space.

### 4.8.7 Modifiers

- Class and member modifiers, when present, appear in the order recommended by the Java Language Specification:

  ```java
  public protected private abstract default static final transient volatile synchronized native strictfp
  ```

### 4.8.8 Numeric Literals

- `long` -valued integer literals use an uppercase `L` suffix, never lowercase (to avoid confusion with the digit `1`). For example, `3000000000L` rather than `3000000000l`.

### 5.2.1 **Package names**

- Package names are all lowercase, with consecutive words simply concatenated together (no underscores). For example, `com.example.deepspace`, not `com.example.deepSpace` or `com.example.deep_space`.

### 5.2.2 Class names

- Class names are written in [UpperCamelCase](https://google.github.io/styleguide/javaguide.html#s5.3-camel-case).
- Class names are typically nouns or noun phrases. For example, `Character` or `ImmutableList`. Interface names may also be nouns or noun phrases (for example, `List`), but may sometimes be adjectives or adjective phrases instead (for example, `Readable`).
- There are no specific rules or even well-established conventions for naming annotation types.
- *Test* classes are named starting with the name of the class they are testing, and ending with `Test`. For example, `HashTest` or `HashIntegrationTest`.

### **5.2.3 Method names**

- Method names are written in [lowerCamelCase](https://google.github.io/styleguide/javaguide.html#s5.3-camel-case).
- Method names are typically verbs or verb phrases. For example, `sendMessage` or `stop`.
- Underscores may appear in JUnit *test* method names to separate logical components of the name, with *each* component written in [lowerCamelCase](https://google.github.io/styleguide/javaguide.html#s5.3-camel-case). One typical pattern is `<methodUnderTest>_<state>`, for example `pop_emptyStack`. There is no One Correct Way to name test methods.

### **5.2.4 Constant names**

- Constant names use `CONSTANT_CASE`: all uppercase letters, with each word separated from the next by a single underscore. But what *is* a constant, exactly?

- Constants are static final fields whose contents are deeply immutable and whose methods have no detectable side effects. This includes primitives, Strings, immutable types, and immutable collections of immutable types. If any of the instance's observable state can change, it is not a constant. Merely *intending* to never mutate the object is not enough.

- Examples:

  ```java
  // Constants
  static final int NUMBER = 5;
  static final ImmutableList<String> NAMES = ImmutableList.of("Ed", "Ann");
  static final ImmutableMap<String, Integer> AGES = ImmutableMap.of("Ed", 35, "Ann", 32);
  static final Joiner COMMA_JOINER = Joiner.on(','); // because Joiner is immutable
  static final SomeMutableType[] EMPTY_ARRAY = {};
  enum SomeEnum { ENUM_CONSTANT }
  
  // Not constants
  static String nonFinal = "non-final";
  final String nonStatic = "non-static";
  static final Set<String> mutableCollection = new HashSet<String>();
  static final ImmutableSet<SomeMutableType> mutableElements = ImmutableSet.of(mutable);
  static final ImmutableMap<String, SomeMutableType> mutableValues =
      ImmutableMap.of("Ed", mutableInstance, "Ann", mutableInstance2);
  static final Logger logger = Logger.getLogger(MyClass.getName());
  static final String[] nonEmptyArray = {"these", "can", "change"};
  ```

  - These names are typically nouns or noun phrases.

## Stepdown Rule

- The rule tells us that the code in our class should be readable from top to bottom, descending one level of abstraction per function. It implies that the function ordering is no longer random. A caller function should always reside above the callee function.

- Bad 😣

  ```java
  private void serve() {
      wife.give(fryingPan.getContents(20, PERCENT));
      self.give(fryingPan.getContents(80, PERCENT)); // huehuehue
  }
  
  private void addEggs() {
      fridge
          .getEggs()
          .forEach(egg -> fryingPan.add(egg.open());
  }
  
  private void cook() {
      fryingPan.mixContents();
      fryingPan.add(salt.getABit());
      fryingPan.mixContents();
  }
  
  public void makeBreakfast() {
     addEggs();
     cook();
     serve();
  }
  ```

- Good 😊

  ```java
  public void makeBreakfast() {
     addEggs();
     cook();
     serve();
  }
  
  private void addEggs() {
      fridge
          .getEggs()
          .forEach(egg -> fryingPan.add(egg.open());
  }
  
  private void cook() {
      fryingPan.mixContents();
      fryingPan.add(salt.getABit());
      fryingPan.mixContents();
  }
  
  private void serve() {
      wife.give(fryingPan.getContents(20, PERCENT));
      self.give(fryingPan.getContents(80, PERCENT));
  }
  ```

## 도구의 지원을 받자

- Style을 정하고 외워서 하는 것이 아니라 도구(IDE)를 사용하자!
  - Eclipse : Preferences - Java - Code Style - Formmatter
    - `.xml` 파일 로드해서 사용
  - IntelliJ : Settings - Editor - Code Style - Java
    - Scheme에서 선택 (GoogleStyle 등)
  - VSCode : ESLint

## White space changes

- Git commit 시 내용이 동일해도 whitespace가 다르면 whitespace changes 발생
  - 불필요한 changes
- 코딩 컨벤션 맞춰서 쓰면 이런 문제가 크게 줄어듦
- 설정에서 Show whitespace changes 선택 해제하면 보이지 않음
  - 하지만 보이지 않을뿐 사라지는 것은 아님
- 컨플릭트 날 때 내용 문제가 아니라 whitespace 문제일 수 있음
  - 팀원들끼리 코딩 컨벤션 잘 지키면 이런 문제는 줄일 수 있다