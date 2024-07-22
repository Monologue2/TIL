# Slices
> 기초 자료 구조 <br>
> 공부 한 내역 업데이트용, A Tour of Go 에서 다양한 Go의 기능과 작동 구조를 상세히 배워 볼 수 있다.

## 본문
`array`는 고정된 크기를 가진다. `slice`는 가변적인 크기를 가지고, `array`의 요소를 유연하게 볼 수 있다.<br>
실제로 `slice`는 `array`보다 훨신 더 일반적입니다.<br>

`slice`는 콜론으로 구분된 하한 및 상한의 두 지수로 구성됩니다.<br>
이 `slice`는 첫번째 요소를 포함하고, 마지막 요소를 포함하지 않는 절반 범위(half-open)를 선택합니다.<br>
`a[1:4]` 는 index 1 부터 index 3가지 요소를 포함합니다. 
``` go
    a[low:high]
    a[1:4]
```

```go
    package main

    import "fmt"

    func main() {
        var primes [10]int = [10]int{0,1,2,3,4,5,6,7,8,9}

        var slice1 []int = primes[2:7]
        slice2 := primes[1:3]

        fmt.Println(slice1, slice2)
    }
```

### Slice는 array의 참조와 유사하다.
`slice`는 어떤 데이터도 저장하지 않고, 기본 `array`의 구획을 설명(describes)할 뿐이다.<br>
`slice`의 요소를 바꾸는건 기본 `array`의 요소를 바꾸는 것과 동일하다.<br>
동일한 기본 `array`를 공유하는 `slices` 들은 데이터 변경 사항을 공유한다.<br>

### Slice Literals
`slice literal`이란 `array literal`에서 길이를 뺀 것과 비슷하다.
```go
    [3]bool{true, true, false} // array literal
    []bool{true, true, false} // slice literal
```

### Slice Default
`slicing`을 할 때 하한 또는 상한을 생략해도 기본값을 대신 사용한다.<br>
기본값은 하한일 때 0 이며, 상한일 때 `slice`의 길이다.<br>
```go
    var a[10]int

    a[0:10]
    a[:10]
    a[0:]
    a[:]
```

### Slice Length and Capacity
`slice`는 `length`와 `capacity`를 가진다.<br>
`length`는 `slice`가 가진 요소의 수를 뜻한다.<br>
`capacity`는 원본 `array`의 요소 수를 뜻하며, `slice`의 첫 번째 요소부터 센다.
`slice`의 `length` 와 `capacity`는 `len(s)`, `cap(s)` 표현식을 통해 얻을 수 있다.

`capacity`가 충분하다면 `re-slicing` 할 수 있다. (원본 `array`의 값을 가져올 수 있다.)

``` go
    package main

    import "fmt"

    func main() {
        s := []int{3,5,6,7,10,20}
        
        s = s[:0]
        printSlice(s) // len=0 cap=6 []

        s = s[:4]
        printSlice(s) // len=4 cap=6 [3,4,5,7]

        s = s[:6]
        printSlice(s) // len=6 cap=6 [3,4,6,7,10,20]
    }

    func printSlice(s []int) {
        fmt.Printf("len=%d, cap=%d, %v\n", len(s), cap(s), s)
    }
```

### Nil Slice
아무 것도 들어있지 않은 `slice`는 `nil` 이다.<br>
`nil slice`는 `capacity`와 `length`가 0이며, 원본 `array`가 존재하지 않는다.<br>
```go
    var s []int
    fmt.Println(len(s), cap(s), s)

    if s == nil {
        fmt.Println("nil!")
    }
```

### Create a slice with make
내장 함수인 `make` 로 `slice`를 생성할 수 있다.<br>
`make` 함수는 0으로 선언된 `array`를 참조하는 `slice`를 반환한다.<br>

```go
    a := make([]int, 5) // len(a) = 5
```

세번째 인자는 `capacity`를 지정할 수 있다.
```go
    b := make([]int, 5, 10) // len(b) = 5, cap(b) = 10
```

### Slices of slices
`Slices`는 다른 `slices`를 포함한 어떤 타입도 포함할 수 있다.
```go
    package main

    import (
        "fmt"
        "strings"
    )

    func main() {
        board := [][]string{
            []string{"-","-","-"},
            []string{"-","-","-"},
            []string{"-","-","-"},
        }

        thirdD := [][][]string {
            [][]string{
                []string{"-","-","-"},
                []string{"-","-","-"},
                []string{"-","-","-"},
            },
            [][]string{
                []string{"-","-","-"},
                []string{"-","-","-"},
                []string{"-","-","-"},
            },
            [][]string{
                []string{"-","-","-"},
                []string{"-","-","-"},
                []string{"-","-","-"},
            },
        }

        borad[0][0] = "X"

        for i := 0 ; i < len(board); i++ {
            fmt.Printf("%s\n", strings.Join(board[i], " "))
        }

        fmt.Println(ThirdD)
    }
```

### Appending to a slice
내장 함수 `append`를 사용하여 `slice`에 새로운 요소를 추가하는 보편적인 방법.<br> 

```go
    func append(s []T, vs ...T) []T
    func append(slice []Type, elems ...Type) []Type
```
`append`의 첫 번째 매개변수는 T 타입의 `slice`이며, 나머지는 `slice`에 추가하려는 T 값들이다.<br>
`append`의 결과(반환)값은 기존 요소와 추가로 제공된 값들을 포함한 `slice`이다.<br>

만약 `array`가 너무 작은 capacity를 가진 경우, 더 큰 `array`가 할당된다.



##### Referrences
- [A Tour of Go](https://go.dev/tour/list)
- [Go Slices](https://go.dev/blog/slices-intro)

