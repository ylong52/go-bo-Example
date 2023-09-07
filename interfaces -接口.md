### 接口（Interface）

---
在 Go 语言中，接口（Interface）是一种类型，它定义了一组方法的签名，但没有实现这些方法的代码。接口可以被任何类型实现，只要这些类型实现了接口中定义的方法，就可以被赋值给接口类型的变量。因此，接口在 Go 语言中有着广泛的应用场景，包括但不限于以下几个方面：

- [ ]实现多态性：通过接口实现多态性，可以让相同接口的不同实现在不同时刻表现出不同的行为，从而提高程序的灵活性和可扩展性。

- [ ]抽象数据类型：通过接口定义抽象数据类型，可以隐藏数据结构的具体实现细节，只暴露出必要的方法，从而实现更高层次的抽象和封装。

- [ ]插件系统：通过接口实现插件系统，可以让程序在运行时动态地加载和卸载插件，从而实现更高层次的可扩展性和灵活性。

- [ ]协议实现：通过接口实现协议，可以让程序与其他程序或系统进行通信，从而实现更高层次的互操作性和可移植性。

---

以下是添加中文注释的示例代码：

```go
package main

import (
	"fmt"
	"math"
)

// Geometry 接口定义了几何图形的面积和周长的方法
type Geometry interface {
	area() float64    // 求面积
	perim() float64   // 求周长
}

// Rect 结构体定义了矩形的宽和高
type Rect struct {
	width, height float64   // 宽和高
}

// Circle 结构体定义了圆的半径
type Circle struct {
	radius float64   // 半径
}

// 实现 Rect 结构体的 area() 方法，用于求矩形的面积
func (r Rect) area() float64 {
	return r.height * r.width   // 面积公式：长 * 宽
}

// 实现 Rect 结构体的 perim() 方法，用于求矩形的周长
func (r Rect) perim() float64 {
	return 2*r.width + 2*r.height   // 周长公式：2 * (长 + 宽)
}

// 实现 Circle 结构体的 area() 方法，用于求圆的面积
func (c Circle) area() float64 {
	return math.Pi * c.radius * c.radius   // 面积公式：π * 半径²
}

// 实现 Circle 结构体的 perim() 方法，用于求圆的周长
func (c Circle) perim() float64 {
	return 2 * math.Pi * c.radius   // 周长公式：2 * π * 半径
}

// measure 函数用于计算几何图形的面积和周长
func measure(g Geometry) {
	fmt.Println(g)   // 输出几何图形的类型
	fmt.Println(g.area())   // 输出几何图形的面积
	fmt.Println(g.perim())   // 输出几何图形的周长
}

func main() {
	r := &Rect{3, 4}   // 创建一个矩形实例
	c := &Circle{5}   // 创建一个圆实例

	measure(r)   // 计算矩形的面积和周长
	measure(c)   // 计算圆的面积和周长
}
```


