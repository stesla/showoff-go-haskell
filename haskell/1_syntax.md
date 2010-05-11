!SLIDE center
# Syntax

!SLIDE code
# Functions
    add a b = a + b

    add 5 3   --> 8

    5 `add` 3 --> 8

    add 5     --> function

!SLIDE code
# Operators
    a *+* b = a * a + b * b

    3 *+* 5   --> 34

    (*+*) 3 5 --> 34

    (3 *+*)   --> function

    (*+* 5)   --> function

!SLIDE code
# Matching
    if' True  a _  = a
    if' False _ b  = b

# Conditions
    isEven x when x `rem` 2 == 0 -> True
                | otherwise      -> False

!SLIDE code
# Lists
    [1, 2, 3]

    ['a', 'b', 'c']

    [1, 'a'] -- WRONG!

# Matching Lists
    map' f [x]    = [f x]
    map' f (x:xs) = (f x) : (map' f xs)

!SLIDE bullets incremental
# Other Syntax
* `let` and `where`
* `case` complete with matching
* `if` but only with `else`
* `do`-notation for use with monads