## 람다 표현식

```
람다 표현식은 매개 변수 목록 ex) (int x, int y) , 화살표 토큰 -> , 처리식ex) x + y
@FunctionalInterface를 사용하면 이 인터페이스에는 내용이 없는 메소드 하나만 선언이 가능



@FunctionalInterface
public interface Calculate {
    int operation(int a, int b);
}




public class LambdaEx {

    public static void main(String[] args) {
        LambdaEx lambdaEx = new LambdaEx();
        lambdaEx.calculateAdd();
        lambdaEx.calculateSubtract();
        lambdaEx.runCommonThread();
        lambdaEx.runThread();
        lambdaEx.runThreadSimple();
    }

    private void calculateAdd() {
        Calculate add = (a, b) -> a + b;
        System.out.println(add.operation(1,2));
    }

    private void calculateSubtract() {
        Calculate subtract = (a, b) -> a - b;
        System.out.println(subtract.operation(1, 2));
    }

    private void runCommonThread() {
        Runnable runnable = new Runnable() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName());
            }
        };

        new Thread(runnable).start();
    }

    private void runThread() {
        new Thread(() -> {
            System.out.println(Thread.currentThread().getName());
        }).start();
    }

    private void runThreadSimple() {
        new Thread(() -> System.out.println(Thread.currentThread().getName())).start();
    }

}
```

## java.util.function 패키지

1. Predicate
- test()
- and()
- negate()
- or()

2. Supplier
- get()

3. Consumer
- accept()
- andThen()

4. Function()
- apply()


## stream

스트림은 컬렉션에서 사용가능 배열에서는 사용불가능
배열을 컬렉션의 리스트로 변환후 스트림을 사용할 수 있다.

```
public class StudentDTO {

    private String name;
    private int age;
    private int scoreMath;
    private int scoreEnglish;

    public StudentDTO(String name, int age, int scoreMath, int scoreEnglish) {
        this.name = name;
        this.age = age;
        this.scoreMath = scoreMath;
        this.scoreEnglish = scoreEnglish;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public int getScoreMath() {
        return scoreMath;
    }

    public int getScoreEnglish() {
        return scoreEnglish;
    }

}



import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StudentForEachSample {

    public static void main(String[] args) {
        StudentForEachSample sample = new StudentForEachSample();
        List<StudentDTO> studentList = new ArrayList<>();
        studentList.add(new StudentDTO("요다", 43, 99, 10));
        studentList.add(new StudentDTO("만두", 30, 71, 85));
        studentList.add(new StudentDTO("건빵", 32, 81, 75));
        //sample.printStudentNames(studentList);

        //배열 -> List 컬렉션으로 변환
        Integer[] values = {1, 3, 5};
        //List<Integer> list = new ArrayList<>(Arrays.asList(values));
        //sample.printArray(list);

        List<Integer> list = Arrays.stream(values).collect(Collectors.toList());
        sample.printArray(list);
    }

    //출력하는 방법 4가지
    public void printStudentNames(List<StudentDTO> students) {
        students.stream().forEach(student -> System.out.println(student.getName()));

        for (StudentDTO studentDTO : students) {
            System.out.println(studentDTO.getName());
        }

        students.stream().map(student -> student.getName()).forEach(x -> System.out.println(x));

        students.stream().map(student -> student.getName()).forEach(System.out::println);
    }

    public void printArray(List<Integer> list) {
        list.stream().forEach(System.out::println);
    }


}

```


```
mport java.util.Arrays;
import java.util.stream.Stream;

public class MethodReferenceSample {

    public static void main(String[] args) {
        MethodReferenceSample sample = new MethodReferenceSample();
        String[] stringArray = {"요다", "만두", "건빵"};
        //sample.staticReference(stringArray);
        sample.objectReference(stringArray);
    }

    private static void printResult(String value) {
        System.out.println(value);
    }

    private void staticReference(String[] stringArray) {
        Stream.of(stringArray).forEach(System.out::println);
        Stream.of(stringArray).forEach(MethodReferenceSample::printResult);
    }

    private void objectReference(String[] stringArray) {
        Arrays.sort(stringArray, String::compareToIgnoreCase);
        Arrays.asList(stringArray).stream().forEach(System.out::println);
    }

}

```


