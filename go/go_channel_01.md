channels操作默认是阻塞的，发送和接受必须两边都准备好。

比如代码：
```go
package main
import "fmt"

func main() {
  ch := make(chan int)
  ch <- 3
  fmt.Println(<-ch)
}
```
运行会报：fatal error: all goroutines are asleep - deadlock!

因为在main goroutine中 想要发送 3 -> ch，接受 <-ch 必须准备好。这情况接受没有准备好
所以阻塞在 ch <- 3这里。导致main死锁。
