# Object 클래스에서 제공하는 메소드 종류

```
protected Object clone() : 객체의 복사본을 만들어 리턴한다.
public boolean equals(Object obj) : 현재 객체와 매개 변수로 넘겨 받은 객체가 같은지 확인. 같으면 true, 틀리면 false를 리턴한다.
public Class <?> getClass() : 현재 객체의 Class 클래스의 객체를 리턴
public int hashCode() : 객체에 대한 해시 코드 값을 리턴. 해시 코드라는 것은 16진수로 제공되는 객체의 메모리 주소를 말한다.
public String toString() : 객체를 문자열로 표현하는 값을 리턴한다.
```

# ==, equals

```
==은 주로 기본자료형이 같은지 비교하는 연산자
==이 참조자료형을 비교할 때는 값을 비교하는 것이 아닌 주소값을 비교한다.
Object에 있는 equals메소드를 오버라이디하지 않을 경우 ==과 똑같이 주소값을 비교하게 되고 오버라이딩을 하면 값을 비교하게 된다.
Object에 선언되어 있는 equals메소드는 해시코드값을 비교한다. 해시코드 값은 해당 객체의 주소값을 리턴한다.
String클래스에 있는 equals는 값을 비교한다.(값을 비교하도록 오버라이딩을 했기 떄문이다.
따라서 equals메소드를 오버라이딩을 할시 hashcode메소드도 같이 오버라이딩을 해야한다.
```


