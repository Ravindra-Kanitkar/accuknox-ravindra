
# Assignment Explaination

First of all, thank you for allowing me to participate in the initial screening round. Below are the detailed answers to all the questions you asked.

## Problem statement 1 and 2: Drop packets using eBPF

I am not very well versed in eBPF, and frankly, I found these concepts difficult to grasp. However, I can assure you that I learn quickly. Unfortunately, I am unable to answer this question at this time. I could have taken help from ChatGPT or Gemini, but I believe that trust is an important factor at this stage, and I want to present myself as I am. I am more focused on problem-solving, which will enable me to grasp more concepts effectively.

## Problem statement 3: Drop packets using eBPF

This is the code that you gave it to me for explaination :- 

package main
import "fmt"
```go
func main() {
    cnp := make(chan func(), 10)
    for i := 0; i < 4; i++ {
        go func() {
            for f := range cnp {
                f()
            }
        }()
    }
    cnp <- func() {
        fmt.Println("HERE1")
    }
    fmt.Println("Hello")
}
```

So, I am writing all the answers of respective questions.

First, we create a buffered channel of type func using the make command, allowing functions to be stored in it using goroutines. Then, we run a loop four times, and within each iteration, we spawn a goroutine. Each goroutine checks for values in the cnp channel. Since the channel is initially empty, the goroutines will wait for functions to be sent to the channel. At this point, there are four goroutines waiting to receive their respective functions to execute.

Next, we pass a function into the channel and then print "Hello". As a result, only "Hello" will be printed, as explained in the answer to question 4.

The statement "HERE1" will not be printed because all the goroutines are waiting for a function. Once the function is passed into the channel, "Hello" is printed immediately. Since the program ends and we are not using any waitgroups, the program finishes its execution before the goroutines have a chance to complete their tasks.




