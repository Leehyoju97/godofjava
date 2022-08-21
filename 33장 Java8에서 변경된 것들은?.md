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



