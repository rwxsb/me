## Slices on Go
In Go slice retains the underlying array, this is particularly interesting. We are able to shrink then extend a slice.

```go
s := []int{2, 3, 5, 7, 11, 13}
printSlice(s)

// Slice the slice to give it zero length.
s = s[:0]
printSlice(s)
//len=0 cap=6 []
// Extend its length.
s = s[:4]
printSlice(s)
//len=4 cap=6 [2 3 5 7]
```

#golang
