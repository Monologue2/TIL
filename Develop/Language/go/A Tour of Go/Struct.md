# Structs
> 기초 자료 구조 <br>
> 공부 한 내역 업데이트용, A Tour of Go 에서 다양한 Go의 기능과 작동 구조를 상세히 배워 볼 수 있다.

### 본문
**`struct`는 field의 모음이다.**
``` go
    package main

    type Vertex struct {
        X int
        Y int
    }

    func main() {
        fmt.Println(Vertex{1,2})
        var A Vertex = Vertex{1,2}
        A = Vertex{3,4}
        fmt.Println(A)

        B := Vertex{5,6}
        fmt.Println(B)
    }
```

**`struct field` 는 `.` 을 통해 접근한다.**
``` go
    // ...
    func main() {
        v := Vertex{1,2}
        v.X = 3
        fmt.Println(v.X) // 3
    }
```

**`struct pointer`를 통해 `struct field`에 접근 할 수 있다.**
``` go
    // ...
    func main() {
        v := Vertex{1,2}
        p := &v
        p.X = 1e10
        p.Y = 20

        fmt.Println(v)
        fmt.Println(*p)
    }
```

**`struct litertal`은 struct의 값을 나열하여 새로 할당된 `struct value` 을 나타낸다.**<br>
`Name:` 문법을 통해 `struct field`의 부분만 선언할 수 있다.<br>
특수 접두사 `&` 는 `struct value`의 pointer를 반환한다.<br>
``` go
    package main

    import "fmt"

    type Vertex struct {
        X int
        Y int
    }

    type Test struct {
        MyValue int
        MyString string
        MyFloat float64
    }

    var (
        v1 = Vertex{1, 2}
        v2 = Vertex{Y: 1}
        v3 = Vertex{} // X:0, Y:0
        p = &Vertex{1,2}

        t1 = Test{MyValue:10, MyString:"유승언", MyFloat:10.2512513}
    )

    func main() {
        fmt.Println(v1, v2, v3) // {1 2} {1 0} {0 0} 
        fmt.Println(p) // &{1 2} , Struct value의 Pointer 반환을 뜻하는 접두사
        fmt.Println(t1)
    }
```


##### Referrences
- [A Tour of Go](https://go.dev/tour/list)

