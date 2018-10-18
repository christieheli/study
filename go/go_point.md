go结构体方法，方法内改变结构体指针地址无效？

比如代码：
```go
package main
import "fmt"

type linkNode struct {
	data     int64
	nextNode *linkNode
}

type LinkList struct {
	linkNode
}

func (l *LinkList) create() *LinkList {
	var headNode *LinkList
	headNode = new(LinkList)
	headNode.data = 0
	headNode.nextNode = nil
	l = headNode
	return headNode
}

func main() {
	var l *LinkList
  l.create()
  // l = l.create()
  if l == nil {
		panic("linkList is nil")
	}
	
}
```
运行会报：panic: linkList is nil

运行 29行代码就正常
