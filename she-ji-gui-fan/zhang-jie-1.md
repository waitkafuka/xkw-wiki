# 章节1

## 设计规范章节1

### 列表符号、链接

```text
- 安装插件：<https://toolchain.gitbook.com/plugins/>
- 更换主题：<https://toolchain.gitbook.com/themes/>
- 生成离线：<https://toolchain.gitbook.com/ebook.html>
```

效果：

* 安装插件：[https://toolchain.gitbook.com/plugins/](https://toolchain.gitbook.com/plugins/)
* 更换主题：[https://toolchain.gitbook.com/themes/](https://toolchain.gitbook.com/themes/)
* 生成离线：[https://toolchain.gitbook.com/ebook.html](https://toolchain.gitbook.com/ebook.html)

### 一级标题

代码： `# 这是一级标题`  
效果：

## 这是一级标题

二级标题为两个`#`，1-6个，以此类推。

### 换行

在末尾敲两个空格。

### 嵌入代码

代码：

```text
`code`
```

效果：  
`code`

### 字体加粗

代码：

```text
**字体加粗**
```

效果：  
**字体加粗**

### 字体倾斜

代码：

```text
*字体倾斜*
```

效果： _字体倾斜_

### 字体加粗又倾斜

代码：

```text
***字体加粗又倾斜***
```

效果：  
_**字体加粗又倾斜**_

### 插入图片

代码：

```text
![](http://zxxkstatic.zxxk.com//zxxk/skins/index/images/Month/3.jpg)
```

效果：  


![](http://zxxkstatic.zxxk.com//zxxk/skins/index/images/Month/3.jpg)

### 插入链接

#### 方式1-快捷方式

代码：

```text
<https://github.com/zitiaocn/simple>
```

效果： [https://github.com/zitiaocn/simple](https://github.com/zitiaocn/simple)

#### 方式2-常规方式

代码：

```text
这是一个[链接](https://github.com/zitiaocn/simple "这里是title属性的值")
```

效果：  
这是一个[链接](https://github.com/zitiaocn/simple)

**如果是链接到同一个主机，还可以使用相对路径**  
**链接中的内容还可以是页面上的ID，这样点击后可以定位到指定锚点**

### 插入图片链接

代码： `[![](http://zxxkstatic.zxxk.com//zxxk/skins/index/images/Month/3.jpg)](https://github.com/zitiaocn/simple)`

效果：  


![](http://zxxkstatic.zxxk.com//zxxk/skins/index/images/Month/3.jpg)

 **即：把链接代码前面的中括号里面写上一个图片**

### 分割线

代码：

效果：

### 块引用

代码：

> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
>
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse id sem consectetuer libero luctus adipiscing.  
> 效果：  
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
>
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse id sem consectetuer libero luctus adipiscing.

### 代码块引用

代码：

```text
    tell application "Foo"
        beep
    end tell 
```

效果：

```text
tell application "Foo"
    beep
end tell
```

**注意：代码开始部分和前面文字必须要有一个空行！**

