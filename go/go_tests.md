# Go Tests

## Writing tests
Writing a test is just like writing a function, with a few rules

- It needs to be in a file with a name like xxx_test.go
- The test function must start with the word Test
- The test function takes one argument only t *testing.T
- To use the *testing.T type, you need to import "testing", like we did with fmt in the other file

run go test to run

# t.Errorf
t.Errorf -> Print Message and Fail the test

# t *testing.TB
For helper functions, it's a good idea to accept a testing.TB which is an interface that *testing.T and *testing.B both satisfy, so you can call helper functions from a test

# t.Helper()
t.Helper() is needed to tell the test suite that this method is a helper. By doing this, when it fails, the line number reported will be in our function call rather than inside our test helper. This will help other developers track down problems more easily

# Testable Examples
Example functions are compiled whenever tests are executed.
Example functions begin with Example (much like test functions begin with Test), and reside in a package's "_test.go" files. 

```go
func ExampleAdd() {
	sum := Add(1, 5)
	fmt.Println(sum)
	// Output: 6
}
```

Notice the special format of the comment, // Output: 6. While the example will always be compiled, adding this comment means the example will also be executed. Go ahead and temporarily remove the comment // Output: 6, then run go test, and you will see ExampleAdd is no longer executed.

# Benchmarking in Go
Writing benchmarks in Go is another first-class feature of the language and it is very similar to writing tests.

```go
func BenchmarkRepeat(b *testing.B) {
	for i := 0; i < b.N; i++ {
		Repeat("a")
	}
}
```
The testing.B gives you access to the cryptically named b.N.
When the benchmark code is executed, it runs b.N times and measures how long it takes.

To run the benchmarks do go test -bench=. (or if you're in Windows Powershell go test -bench=".")

Note: By default benchmarks are run sequentially.

Note: Sometimes, Go can optimize your benchmarks in a way that makes them inaccurate, such as eliminating the function being benchmarked. Check your benchmarks to see if the values make sense. If they seem overly optimized, you can follow the strategies in this blog post.

# Go Test Cover
Go's built-in testing toolkit features a coverage tool. Whilst striving for 100% coverage should not be your end goal, the coverage tool can help identify areas of your code not covered by tests. If you have been strict with TDD, it's quite likely you'll have close to 100% coverage anyway.

``` bash
go test -cover
```