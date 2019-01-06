# struct

Struct types are user-defined types. Note that no comma is used to separate the fields

```
type example struct {
    flag bool
    counter int16
    pi float32
}
```

Create a Struct with 0 values

    var e1 example

Create a Struct with values. Note that when assigning values, comma is used to separate fields, including the last comma.

```
e2 := example {
    flag: true,
    counter: 10,
    pi: 3.141592, // DON'T FORGET THIS COMMA!
}
```

Anonymous Struct with 0 values

```
var e1 struct {
    flag bool
    counter int32
    pi float32
}
```

Anonymous Struct with values (also known as LITERAL TYPE)

```
e2 := struct {
    flag bool
    counter int32
    pi float32
}{
    flag: false,
    counter: 8,
    pi: 3.14,
}
```

Struct explicit conversion

Go does not do implicit conversion, but it forces to declare conversion explicitly.

```
type a struct  {
    counter int16
    ...
}
type b struct  {
    counter int16
    ...
}
var myA a
var myB b
myB = myA // ERROR!
myB = b(myA) // OK!
```

When using Literal Types, Go converts implicitly.

```
type bob struct { 
    flag bool 
    counter int32 
    pi float32 
}
funct main() {
    e1 := struct { // LITERAL TYPE
        flag    bool
        counter int32
        pi      float32
    }{
        flag:    false,
        counter: 8,
        pi:      3.14,
    }
    var e2 bob
    e2 = e1 // IMPLICIT CONVERSION
    fmt.Println(e2)
}
```
## Struct alignment and padding

<https://medium.com/@felipedutratine/how-to-organize-the-go-struct-in-order-to-save-memory-c78afcf59ec2>


