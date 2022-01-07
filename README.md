##  Spring Boot / JPA (입문)

### H2 Database
개발이나 테스트용도로 가볍고 편리한 DB, web admin 화면 제공

### Lambda
- JAVA 8에서 공식적으로 추가된 표현식
- 익명 함수(Anonymous Functions)
- 함수를 하나의 식으로 표현한 것
- 장점 : 코드의 간결화, 함수의 생성 과정없이 한번에 처리할수 있어 생산성 높아짐
- 단점 : 남발하면 오히려 가독성이 떨어짐, 만든 무명함수는 재사용 불가능
- 함수형 인터페이스(@FunctionalInterface)<br>
 => 함수를 1급 객체처럼 다룰수 있게 해주는 어노테이션, 인터페이스에 선언하여 단 하나의 추상 메소드를 갖도록 제한

- 기존
```java
 public class Lambda { 
  public static void main(String[] args) {
   // 기존의 익명함수 
   System.out.println(new MyLambdaFunction() {
    public int max(int a, int b) {
     return a > b ? a : b; 
    } 
   }.max(3, 5)); 
  } 
 }
 
//출처: https://mangkyu.tistory.com/113 [MangKyu's Diary]
```
- @FunctionalInterface
```java
@FunctionalInterface
interface MyLambdaFunction { 
 // FunctionlInterface는 해당 인터페이스가 1개의 함수만을 갖도록 제한
 int max(int a, int b);
} 

public class Lambda { 
 public static void main(String[] args) { 
  // 람다식을 이용한 익명함수 
  MyLambdaFunction lambdaFunction = (int a, int b) -> a > b ? a : b; 
  System.out.println(lambdaFunction.max(3, 5)); 
 } 
}

//출처: https://mangkyu.tistory.com/113 [MangKyu's Diary]
```

- Java에서 제공하는 함수형 인터페이스(CHECKKKKKKKKKKK!)<br>
Supplier<T><br>
Consumer<T><br>
Function<T, R><br>
Predicate<T>

### JPA
- spring.jpa.show-sql=true<br>
 => JPA가 생성하는 SQL을 출력
- spring.jpa.hibernate.ddl-auto=none<br>
 => JPA는 테이블을 자동으로 생성하는 기능을 제공하는데 none을 사용하면 해당 기능을 끈다. (<-> create)

### * 생각해볼것
- 사실 중요한 것은 @Autowired, @Component.. 를 어떻게 사용하는지가 아닌, 스프링 컨테이너가 왜 나왔고 왜 쓰는건지를 아는것이 중요!
