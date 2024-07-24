# Function
> 기초 자료 구조 <br>
> 공부 한 내역 업데이트용, A Tour of Go 에서 다양한 Go의 기능과 작동 구조를 상세히 배워 볼 수 있다.

## 본문
`Function`은 다른 것과 마찬가지로 `value`(값) 입니다.<br>
`Function`은 다른 `value`들과 마찬가지로 전달 가능합니다.

`Function value`는 종종 다른 `function argument` 또는 `return values`로 사용된다.

```go
    package main

    import (
        "fmt"
        "math"
    )

    func compute(fn func(float64, float64) float64) float64 {
        return fn(3,4)
    }

    func main() {
        hypot := func(x, y float64) float64 {
            return math.Sqrt(x*x + y*y)
        }
        fmt.Println(hypot(5,12))

        // function argument로 전달되는 function value
        fmt.Println(compute(hypot))
        fmt.Println(compute(math.Pow))
    }
```

### Function closures (클로저)
Go `function`은 `closure`일 수 있다.<br>
`closure`는 본문 외부에서 변수를 참조하는 `function value`이다.

해당 `function`은 참조된 변수에 접근하거나 등록할 수 있다. <br>
이 때 `function`은 참조된 변수에 `bound`(바인딩) 한다.

예제에서 `adder` 함수는 `closure`를 반환한다.<br>
각 `closure`는 자신들의 `sum` 변수에 `bound`한다.
```go
    package main

    import fmt

    // Closure를 return 하는 형태
    func adder() func(int) int {
        sum := 0
        return func(x int) int  {
            sum += x
            return sum
        }
    }
    
    //익숙치 못한 함수 사용법이다. 잘 알아두고 사용할 곳을 궁리해보자.
    func main() {
        // 각 closure 선언, sum 을 0 으로 초기화 한 상태에서 넘겨준다.
        pos, neg := adder(), adder()
        for i := 0; i < 10; i+ {
            fmt.Println(
                // 각 closure는 개별 sum을 가지고 있다.
                pos(i),
                neg(2*i)
            )
        }
    }
```

#### 번외 : Exercise: Fibonacci Closure
```go
    package main

    import "fmt"

    // fibonacci is a function that returns
    // a function that returns an int.
    func fibonacci() func() int {
        var prev, cur int
        prev = 0
        cur = 1
        
        return func() int {
            prev, cur = cur, cur + prev
            return cur
        }
    }

    func main() {
        f := fibonacci()
        for i := 0; i < 10; i++ {
            fmt.Println(f())
        }
    }
```


##### References
- [A Tour of Go](https://go.dev/tour/list)