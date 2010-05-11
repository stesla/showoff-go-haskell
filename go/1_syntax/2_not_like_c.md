!SLIDE bullets incremental
# Go Is Not Like C #
* Semi-colons optional
* Variable declarations
* There is only `for`
* `switch` got an overhaul
* functions have multiple return values

!SLIDE code
# Variable Declarations #
    /* In C */
    int* a, b;

    /* You probably meant */
    int *a, *b;

    /* In Go */
    var a, b *int;

!SLIDE code
# Variable Initialization #
    var b int = 1;

    var b = 1;

    b := 1;

!SLIDE code
# `for` loop syntax
    for i = 0; i < MAX; i++ { /* ... */ }

    for j > MIN { /* ... */ }

    for i, s = range "hello" { /* ... */ }

    for { /* ever */ }

!SLIDE center
# `switch` syntax

!SLIDE code
# Ugly C
    int result;
    switch (byte) {
    case 'a':
    case 'b':
      {
        result = 1;
        break
      }

    default:
      result = 0
    }

!SLIDE code
# Pretty Go
    var result int
    switch byte {
    case 'a', 'b':
      result = 1
    default:
      result = 0
    }

!SLIDE code
# More Ugly C
    int result = calculate();
    if (result < 0) {
      /* negative */
    } else if (result > 0) {
      /* positive */
    } else {
      /* zero */
    }

!SLIDE code
# More Pretty Go
    switch result := calculate(); true {
    case result < 0:
      /* negative */
    case result > 0:
      /* positive */
    default:
      /* zero */
    }

!SLIDE center
# Functions #

!SLIDE code
# Basic Functions
    /* In C */
    int add(int a, b) { return a + b }
    
    /* In Go */
    func add(a, b int) int { return a + b }

!SLIDE code
# Multiple Return Values
    func divide(a, b int) (int, int) {
      quotient := a / b
      remainder := a % b
      return quotient, remainder
    }

!SLIDE code
# Anonymous Functions With Closure
    func makeAdder(x int) (func(int) int) {
      return func(y int) int { return x + y }
    }

    func main() {
      add5 := makeAdder(5)
      add36 := makeAdder(36)
      fmt.Println("The answer:", add5(add36(1))) //=> The answer: 42
    }
