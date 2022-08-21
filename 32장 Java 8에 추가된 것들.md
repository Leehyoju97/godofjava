# Java8의 새로운 것들

- 람다표현식
- 함수형 인터페이스
- 스트림
- 옵셔널
- 인터페이스의 default method
- 날짜 관련 클래스
- 병령 배열 정렬
- StringJoiner

## Optional
- nullpointerexception을 방지하기 위해 사용

## default method
- 이전 버전에서는 인터페이스 안에는 메소드를 구현 할 수 없었지만 java8버전부터는 인터페이스 안에 default method 사용 가능
- 하위 호환성 떄문에 사용하게 됨

## 병렬 배열 정렬
- binarySearch() : 배열 내에서의 검색
- copyOf() :  배열의 복제
- equals() : 배열의 비교
- fill() : 배열 채우기
- hashCode() : 배열의 해시코드 제공
- sort() : 정렬
- toString() : 배열 내용을 출력

sort()는 단일 쓰레드 수행, parallelSort()는 필요에 따라 여러 개의 쓰레드로 나뉘어 작업을 수행

## StringJoiner
- 문자열 사이에 구분자를 추가할 떄 사용
- 스트림 람다식과 같이 사용하여 간결하게 코드 작성 가능

```
public void withCollector(String[] stringArray) {
        List<String> stringList = Arrays.asList(stringArray);
        String result = stringList.stream().collect(Collectors.joining(","));
        System.out.println(result);
    }
```    
