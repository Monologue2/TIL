# Map
> 기초 자료 구조 <br>
> 공부 한 내역 업데이트용, A Tour of Go 에서 다양한 Go의 기능과 작동 구조를 상세히 배워 볼 수 있다.

## 본문

`map`은 키를 값에 매핑한다.<br>
`map`은 아무런 값을 가지지 않은 경우 `nil` 이다.<br.>
`nil map`은 키를 가지고 있지 않고, 키를 추가할 수 없다.

`make` 함수는 주어진 `type`의 `map`을 반환하며, 초기화된 상태로 사용할 준비가 되어있다.<br>


```go
    package main

    import "fmt"

    type Vertex struct {
        Lat, Long Float64
    }

    var m map[string]Vertex

    func main() {
        m = make(map[string]Vertex)
        m["Bell Labs"] = Vertex {
            40.68433, -74.39967,
        }
        fmt.Println(m["Bell Labs"]) //{40.68433 -74.39967}
    }
```

### Map Literal
`map literal`은 `struct literal` 과 유사하지만 `key`를 요구한다.

```go
    package main

    import "fmt"

    type Vertex struct {
        Lat, Long float64
    }

    // [Key]ValueType
    var m = map[string]Vertex{
        "Bell Labs" : Vertex{
            40.68433, -74.39967,
        },
        "Google" : Vertex{
            37.42202, -122.08408,
        }
    }

    func main() {
        fmt.Println(m)
    }
```
<br>
만약 `top-level type`이 단순히 `type name`이라면 literal의 요소에서 생략할 수 있다.

``` go
    package main

    import "fmt"

    type Vertex struct {
        Let, Long float64
    }

    // "Bell Labs" : Vertex{...} 에서 타입 명이 omit 되었다.
    var m = map[string]Vertex{
        "Bell Labs" : {40.68433, -74.39967},
        "Google" : {37.42202, -122.08408}
    }

    func main() {
        fmt.Println(m)
    }
```

### Mutating Maps
`map` `m`에 삽입 또는 업데이트를 해야 할 때 :
``` go
    m[key] = elem
```

`key`를 검색할 때 :
```go
    elem = m[key]
```

`element`를 삭제할 때 :
```go
    delete(m, key)
```

`two-value assignment` 두 값 할당을 통해 현재 키가 있는지 테스트 할 때 :<br>
`key`가 `m`에 존재할 경우 `ok`는 `true`를 반환한다, 아닐 경우 `false`를 반환한다.<br>
```go
    elem, ok = m[key]
```

만약 `elem`과 `ok`가 선언되지 않았을 경우 `short declaration form`을 사용하라.
```go
    elem, ok := m[key]
```

```go
    package main

    import "fmt"

    type Vertex struct {
        X, Y int
    }

    func main() {
        m := make(map[string]Vertex)

        m["First"] = Vertex{1,2}
        m["Second"] = Vertex{2,3}

        elem, ok := m["Third"]
        fmt.Println(elem, ok)

        m["First"] = Vertex{4,5}
        delete(m, "Second")
        fmt.Println(m["First"])
        elem, ok = m["Second"]
        fmt.Println(elem, ok)
    }
```