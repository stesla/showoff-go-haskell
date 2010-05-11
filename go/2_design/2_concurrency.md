!SLIDE center
# Concurrency #

!SLIDE center
## Do not communicate by sharing memory; instead, share memory by communicating.

!SLIDE bullets incremental
# Concurrency Essentials
* Goroutines execute code
* Channels communicate

!SLIDE code
# Goroutines
    go DoThis() // but do not wait

    go func() {
      for { /* do something forever */ }
    }() // You must call the function

!SLIDE code smaller
# Channels
    /* Create channels with make, not new */
    ch := make(chan int)

    /* Sending a value blocks until the value is read */
    ch <- 4

    /* Reading a value blocks until a value is available */
    i := <-ch

!SLIDE code
# Example
    ch := make(chan int)
    
    go func() {
      result := 0
      for i := 0; i < 100000000; i++ {
        result = result + i
      }
      ch <- result
    }()
    
    /* Do something for a while */
    
    sum := <-ch
    fmt.Println("The sum is:", sum)