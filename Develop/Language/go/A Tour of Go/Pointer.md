# Pointer
> 기초 자료 구조 <br>
> 과거 공부 한 내역 업데이트용, A Tour of Go 에서 다양한 Go의 기능과 작동 구조를 상세히 배워 볼 수 있다.

### 정의
 `&`(주소 연산자, Address Operator) : 변수의 **메모리 주소 반환**<br>
 `*`(역참조 연산자, Dereference Operator) :포인터가 가리키는 **메모리 주소에 저장된 값 반환** <br>

 ### 본문
Go는 포인터 기능을 가지고 있습니다. 포인터는 값의 메모리 주소를 가집니다. <br>
`*T` 타입은 `T` 값의 포인터입니다.  비어 있는 경우 `nil` 입니다. <br>

``` go
    var p *int
```

`&` 연산자는 피연산자의 포인터를 생성합니다.
``` go
    i := 42
    p = &i
``` 

`*` 연산자는 포인터의 값을 나타냅니다. 이를 역참조라 합니다.
``` go
    fmt.Println(*p)
    *p = 21
```

**C 와 달리 Go는 포인터 연산이 없습니다.**

### 활용
1. 효율적인 메모리 사용<br>
    함수에 큰 Struct 를 전달할 때 포인터를 사용하면, Call by Reference 로 호출할 수 있다.<br>
    메모리 사용을 줄이고 성능을 향상시킬 수 있다.
    ```go
        func processStruct(s *Mystruct) {
            // Some Logics...
        }
    ```

2. 함수의 다중 반환, 공유 메모리<br>
    포인터를 사용하면 함수에서 변수 자체를 수정할 수 있다. <br>
    또한 여러 개의 함수나 고루틴이 동일한 데이터를 공유할 수 있다.
    ```go
        func updateValue(p *int) {
            *p = 10
        }
    ```
3. 동적 메모리 할당<br>
    Runtime에 메모리를 동적으로 할당할 때 포인터가 필요하다. <br>
    Go 의 `new` 함수나 `make` 함수를 사용하여 동적으로 메모리를 할당할 수 있다.
    ``` go
        p := new(int)
        *p = 100
    ```

4. 자료 구조 구현<br>
    Linked List, Tree, Graph 등의 자료 구조를 구현할 때 포인터를 사용한다.<br>
    이러한 자료 구조는 각 요소가 다른 요소를 가리키는 포인터를 통해 연결된다.<br>
    ``` go
        type Node struct {
            Value int
            Next *Node
        }
    ```

5. 최적화<br>
    불필요한 데이터 복사를 피하여 최적화 가능하다.<br>
    대규모 데이터 처리나 성능이 중요한 시스템에서 사용한다.


##### Referrences
- [A Tour of Go](https://go.dev/tour/list)

