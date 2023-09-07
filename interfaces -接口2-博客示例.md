### interfaces -接口2-博客示例
#### 实现一个简单的博客系统，支持多种类型的文章发布

---

在这个示例中，我们定义了一个接口类型 Article，它有一个方法 Publish()，用于发布文章。然后，我们定义了两个结构体类型 TextArticle 和 ImageArticle，它们分别实现了 Article 接口的 Publish() 方法。在 main() 函数中，我们创建了一个 Article 类型的切片 articles，用于存储多篇文章。然后，我们向切片中添加多篇文章，包括一篇文本文章和一篇图片文章。最后，我们遍历切片，依次调用每篇文章的 Publish() 方法，输出每篇文章的发布信息。

---

```
package main

import (
    "fmt"
)

// 定义一个接口类型 Article，它有一个方法 Publish()，用于发布文章
type Article interface {
    Publish()
}

// 定义一个结构体类型 TextArticle，它实现了 Article 接口的 Publish() 方法
type TextArticle struct {
    Title   string
    Content string
}

func (a TextArticle) Publish() {
    fmt.Printf("Publishing a text article with title=%s, content=%s\n", a.Title, a.Content)
}

// 定义一个结构体类型 ImageArticle，它实现了 Article 接口的 Publish() 方法
type ImageArticle struct {
    Title string
    Image string
}

func (a ImageArticle) Publish() {
    fmt.Printf("Publishing an image article with title=%s, image=%s\n", a.Title, a.Image)
}

func main() {
    // 创建一个 Article 类型的切片，用于存储多篇文章
    articles := make([]Article, 0)

    // 向切片中添加多篇文章
    articles = append(articles, TextArticle{Title: "Text article 1", Content: "This is a text article."})
    articles = append(articles, ImageArticle{Title: "Image article 1", Image: "https://example.com/image.jpg"})

    // 遍历切片，依次调用每篇文章的 Publish() 方法
    for _, a := range articles {
        a.Publish()
    }
}

```
