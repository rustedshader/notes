# GO Notes

Go is a statically typed language

In Go, when you call a function or a method the arguments are copied.



## Go Documentation

Go has a built-in tool, doc, which lets you examine any package installed on your system, or the module you're currently working on.
### Example
```go
go doc fmt
```
### PKG Site

Go's second tool for viewing documentation is the pkgsite command, which powers Go's official package viewing website.

## Concate string in Go

"Hello " + name

## Comment Line in Go

Use -> // 

## Shortening function arguments

Instead of (got string,want string) we can have (got,want string)

## If Statements in Go

```go
if (hi == "hello"){
	fmt.Printf("Hello World")
}
```

## Switch statements in Go

When you have lots of if statements checking a particular value it is common to use a switch statement instead. We can use switch to refactor the code to make it easier to read and more extensible if we wish to add more language support later

```go
func Hello(name,language string)string{
if name == "" {
	name = "World"
}
prefix := englishHelloPrefix
switch language {
	case spanish:
		prefix = spanishHelloPrefix
	case french:
		prefix = frenchHelloPrefix
	default:
		prefix = englishHelloPrefix
}
return prefix + name

}
```

## Refactor Refactor and Refactor There is lot to refactor
instead of 
```go
const french = "Bonjour"
const english = "Hello"
```
you can  
```go
const (
	french = "Bonjour"
	english = "Hello"
)
```

## pkgsite in Go

Navigate to your project's directory, then run pkgsite -open ., which should open a web browser for you, pointing to http://localhost:8080. Inside here you'll see a list of all of Go's Standard Library packages, plus Third Party packages you have installed


## Iterations in Go

To do stuff repeatedly in Go, you'll need for. In Go there are no while, do, until keywords, you can only use for. Which is a good thing!

```go
for i:=0;i<5;i++ {
	fmt.Printf("Hello")
}
```

## Arrays and slices in Go

Arrays allow you to store multiple elements of the same type in a variable in a particular order.

arrays can be defined like 

```go
numbers := [5]int{1,2,3,4,5}
```

Arrays have a fixed capacity which you define when you declare the variable. We can initialize an array in two ways:
- [N]type{value1, value2, ..., valueN} e.g. numbers := [5]int{1, 2, 3, 4, 5}
- [...]type{value1, value2, ..., valueN} e.g. numbers := [...]int{1, 2, 3, 4, 5}

### Printing Arrays

range approach
```go
for _,numbers := range numbers {
	fmt.Printf(numbers)
}
```
we can use normal approach too

### Slices in Go 

Allows us to have collections of any size. The syntax is very similar to arrays, you just omit the size when declaring them

```go
mySlice := []int{1,2,3} rather than myArray := [3]int{1,2,3}
```

## Check if two variables are same ?

reflect.DeepEqual which is useful for seeing if any two variables are the same.

```go
func TestSumAll(t *testing.T) {

	got := SumAll([]int{1, 2}, []int{0, 9})
	want := []int{3, 9}

	if !reflect.DeepEqual(got, want) {
		t.Errorf("got %v want %v", got, want)
	}
}

```

* Note: It's important to note that reflect.DeepEqual is not "type safe" - the code will compile even if you did something a bit silly.

* (From Go 1.21, slices standard package is available, which has slices.Equal function to do a simple shallow compare on slices, where you don't need to worry about the types like the above case. Note that this function expects the elements to be comparable. So, it can't be applied to slices with non-comparable elements like 2D slices.)


### Make , Len and Cap

```go
func SumAll(numbersToSum ...[]int) []int {
	lengthOfNumbers := len(numbersToSum)
	sums := make([]int, lengthOfNumbers)

	for i, numbers := range numbersToSum {
		sums[i] = Sum(numbers)
	}

	return sums
}

```

There's a new way to create a slice. make allows you to create a slice with a starting capacity of the len of the numbersToSum we need to work through. The length of a slice is the number of elements it holds len(mySlice), while the capacity is the number of elements it can hold in the underlying array cap(mySlice)

### Append Function

Use the append function which takes a slice and a new value, then returns a new slice with all the items in it.

```go
func SumAll(numbersToSum ...[]int) []int {
	var sums []int
	for _, numbers := range numbersToSum {
		sums = append(sums, Sum(numbers))
	}

	return sums
}
```

### Slices
Slices can be sliced! The syntax is slice[low:high]. If you omit the value on one of the sides of the : it captures everything to that side of it. In our case, we are saying "take from 1 to the end" with numbers[1:]

## Structs, Methods and Interfaces in Go

How to define struct in go ?

```go
type struct_name struct {
	xxxxx
	xxxxx
}
```

example 

```go
type Rectangle struct {
	Width  float64
	Height float64
}
```

use it example 

```go
rectangle := Rectangle{10.0,10.0}
```

---


### Declaring Methods in Go

```go
func (c Circle) Area() float64 {
	return 0
}
```

Syntax -> func (receiverName ReceiverType) MethodName(args)

When your method is called on a variable of that type, you get your reference to its data via the receiverName variable. In many other programming languages this is done implicitly and you access the receiver via this

### Interfaces in Go

```go
type Shape interface {
	Area() float64
}
```

In Go interface resolution is implicit. If the type you pass in matches what the interface is asking for, it will compile.


Declaring interfaces so you can define functions that can be used by different types (parametric polymorphism)

---

## Pointers and Erros in GO 

In Go, when you call a function or a method the arguments are copied.

When calling func (w Wallet) Deposit(amount int) the w is a copy of whatever we called the method from.

Without getting too computer-sciency, when you create a value - like a wallet, it is stored somewhere in memory. You can find out what the address of that bit of memory with &myVal.

The %p placeholder prints memory addresses in base 16 notation with leading 0xs and the  escape character prints a new line. Note that we get the pointer (memory address) of something by placing an & character at the beginning of the symbol.

```go
func (w Wallet) Deposit(amount int) {
	fmt.Printf("address of balance in Deposit is %p \n", &w.balance)
	w.balance += amount
}
```

```bash
address of balance in Deposit is 0xc420012268
address of balance in test is 0xc420012260
```

You can see that the addresses of the two balances are different. So when we change the value of the balance inside the code, we are working on a copy of what came from the test. Therefore the balance in the test is unchanged.
We can fix this with pointers. Pointers let us point to some values and then let us change them. So rather than taking a copy of the whole Wallet, we instead take a pointer to that wallet so that we can change the original values within it.

The difference is the receiver type is *Wallet rather than Wallet which you can read as "a pointer to a wallet".

These pointers to structs even have their own name: struct pointers and they are automatically dereferenced.

---

## %q in Go
When printing a string in Go you can use the verb %q in the format parameters of fmt functions, when available, to safely escape a string and add quotes to it.

### Example

```go
import "fmt"

func main() {
    fmt.Printf("%s\n", "hello") // prints hello
    fmt.Printf("%q\n", "hello") // prints "hello"
    fmt.Printf("%s\n", "hello\n;") // prints hello
//; \n is not escaped
    fmt.Printf("%q\n", "hello\n;") // prints "hello\n;" \n is escaped here
}
```












## Some Temp shit not yet sorted



-------------------------------------------------------------

We use strings.Builder for efficient string concatenation

example

 var sb strings.Builder
	sb.WriteString(API_ROOT_URL)
	sb.WriteString("/annotation/?query=")

	params := make([]string, 0)

	if opts.Entity != "" {
		params = append(params, "entity:"+url.QueryEscape(opts.Entity))
	}
	if opts.Id > 0 {
		params = append(params, fmt.Sprintf("id:%d", opts.Id))
	}
	if opts.Name != "" {
		params = append(params, "name:"+url.QueryEscape(opts.Name))
	}
	if opts.AnnotationContent != "" {
		params = append(params, "text:"+url.QueryEscape(opts.AnnotationContent))
	}
	if opts.Type != "" {
		params = append(params, "type:"+url.QueryEscape(string(opts.Type)))
	}

	sb.WriteString(strings.Join(params, " AND "))

	return sb.String(), nil
