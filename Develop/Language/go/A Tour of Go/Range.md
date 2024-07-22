# Range
> 기초 자료 구조 <br>
> 공부 한 내역 업데이트용, A Tour of Go 에서 다양한 Go의 기능과 작동 구조를 상세히 배워 볼 수 있다.

`for` 루프문의 `range`는 `slice` 또는 `map`을 순회합니다.

`slice`에서 `ranging`할 때 두 값이 매 순회마다 반환됩니다.<br>
첫 번째 값은 `index`이며 두 번째 값은 해당 `index`의 값의 복사본입니다.<br>

```go
    package main

    import "fmt"

    var pow = []int{1,2,3,4,5,6,7,8}

    func main() {
        for i, v := range pow  {
            fmt.Println(i, v)
        }
    }
```

`index` 또는 `value`를 스킵할려면 `_`를 사용하면 됩니다.
```go
    for i, _ := range pow
    for _, v := range pow
```
만약 `index` 값만 원한다면 두 번째 변수를 생략하면 됩니다.
```go
    for i := range pow
```


##### Referrences
- [A Tour of Go](https://go.dev/tour/list)

