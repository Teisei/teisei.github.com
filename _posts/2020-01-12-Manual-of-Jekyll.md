---
layout: post
title: "Manual of Jekyll"
date: 2020-1-12 18:43:00
categories: tech
excerpt: 这部分是文章摘要
---

* content
{:toc}


You’ll find this post in your `_posts` directory.
Jekyll also offers powerful support for code snippets:

	def print_hi(name)
	  puts "Hi, #{name}"
	end
	print_hi('Tom')
	#=> prints 'Hi, Tom' to STDOUT.


Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help


---







![ruby-v]({{ "/images/gifts.jpg"}})  
![ruby-gems]({{ "/css/pics/ruby-gems.png"}})  
![Alt text](/images/gifts.jpg)

<img src="http://i1226.photobucket.com/albums/ee403/teiseidin/Facebook/Cover%20Photos/10253780_621924094561198_2796835470303661060_n_zpszwvpkvjk.jpg" alt="Alt text">

![Alt text][id]
[id]: http://b166.photo.store.qq.com/psb?/V117mrBc1kK848/YiApeL0YhbmKDBoFF.OECudOhfyFMvJSYFVYQXlYsE8!/b/dBvd.mIOCQAA&bo=IAMTAgAAAAABBxI!&rf=viewer_4  "Optional title attribute"



## 可能出现的问题

### `hitimes/hitimes (LoadError)`

**错误代码：**

<pre><code class="markdown">C:/Ruby22/lib/ruby/2.2.0/rubygems/core_ext/kernel_require.rb:54:in `require': cannot load such file -- hitimes/hitimes (LoadError)</code></pre>

**解决方法：**

在stackoverflow上又一个很好的解决方法。[hitimes require error when running jekyll serve on windows 8.1](http://stackoverflow.com/questions/28985481/hitimes-require-error-when-running-jekyll-serve-on-windows-8-1) 虽然上面的题主问的是 win 8.1 系统下的情况，但是同样适用于 win7。下面我简单翻译一下错误原因和解决方法。

> 可能是 Ruby 2.2 和 hitimes-1.2.2-x86-mingw32 中有一些 ABI 变化，少了一些相关的类库。
> 
> 所以卸载 hitimes 并通过 `--platform ruby` 重装即可。代码如下：
>
><pre><code class="markdown">gem uni hitimes
**Remove ALL versions**
gem ins hitimes -v 1.2.1 --platform ruby
</code></pre>
> 然后将自动重新编译 hitimes 并适用于 Ruby 2.2

下面是我自己的卸载和安装过程：

<pre><code class="markdown">E:\GitWorkSpace\gaohaoyang.github.io>gem uni hitimes

You have requested to uninstall the gem:
        hitimes-1.2.2-x86-mingw32

timers-4.0.1 depends on hitimes (>= 0)
If you remove this gem, these dependencies will not be met.
Continue with Uninstall? [yN]  y
Successfully uninstalled hitimes-1.2.2-x86-mingw32

E:\GitWorkSpace\gaohaoyang.github.io>gem ins hitimes -v 1.2.1 --platform ruby
Fetching: hitimes-1.2.1.gem (100%)
Temporarily enhancing PATH to include DevKit...
Building native extensions.  This could take a while...
Successfully installed hitimes-1.2.1
Parsing documentation for hitimes-1.2.1
Installing ri documentation for hitimes-1.2.1
Done installing documentation for hitimes after 1 seconds
1 gem installed</code></pre>



---






#### 重点:
* `SyntaxHighlighter.toolbar.items.list`此变量存放需要toolbar元素,默认有`['expandSource', 'help']`
* 自定义toolbar元素可以参加官方的expandSource元素实现,主要要实现getHtml或execute方法.
  + getHtml返回值将会添加到页面`div.toolbar`里
  + execute用于点击getHtml返回Html所执行的代码
  + 没有getHtml方法时,将会调用defaultGetHtml要方法

###### 官方的expandSource代码
```javascript
  expandSource: {
    getHtml: function(highlighter) {
      if (highlighter.getParam('collapse') != true) return '';

      var title = highlighter.getParam('title');
      return sh.toolbar.getButtonHtml(highlighter, 'expandSource', title ? title : sh.config.strings.expandSource);
    },

    execute: function(highlighter) {
      var div = getHighlighterDivById(highlighter.id);
      removeClass(div, 'collapsed');
    }
  }
```


---


题目给出了 index.html 如下：

	<!DOCTYPE HTML>
	<html>
	<head>
	    <meta http-equiv="Content-Type" content="text/html; charset=gb18030">
	    <title>Untitled Document</title>
	    
	</head>
	<body>
	    <script type="text/javascript">   
	        /*
	         * param1 Array 
	         * param2 Array
	         * return true or false
	         */
	        function arraysSimilar(arr1, arr2){
	        
	        }
	    </script>
	    <script src="testData.js"></script>
	</body>
	</html>

---

* 把 upstream/master 分支合并到本地 master 上，这样就完成了同步，并且不会丢掉本地修改的内容。    
`git merge upstream/master`      

<pre><code>git merge upstream/master
# Updating a422352..5fdff0f
# Fast-forward
#  README                    |    9 -------
#  README.md                 |    7 ++++++
#  2 files changed, 7 insertions(+), 9 deletions(-)
#  delete mode 100644 README
#  create mode 100644 README.md
</code></pre>

---


## CSS 如何工作

[CSS 如何工作](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Getting_started/How_CSS_works) Mozilla 的开发者文档讲的很好。

> 浏览器在展现一个文档的时候，必须要把文档内容和相应的样式信息结合起来展示。 这个处理过程一般分两个阶段：   
>
> 1. 浏览器先将标记语言和 CSS 转换成 DOM (文档对象模型)结构。 这时 DOM 就代表了电脑内存中的相应文档，因为它已经融合了文档内容和相应的样式表。   
> 2. 最后浏览器把 DOM 的内容展示出来。   

---


## 层叠和继承

[参考资料: 层叠和继承](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Getting_started/Cascading_and_inheritance)

> 对于层叠来说，共有三种主要的样式来源：
> 
> * 浏览器对HTML定义的默认样式。
> * 用户定义的样式。
> * 开发者定义的样式，可以有三种形式：
> 	
>	* 定义在外部文件（外链样式）：本教程中案例主要是通过这种形式定义样式。
> 	* 在页面的头部定义（内联样式）：通过这种形式定义的样式只在本页面内生效。
> 	* 定义在特定的元素身上（行内样式）：这种形式多用于测试，可维护性较差。
>
> 用户定义的样式表会覆盖浏览器定义的默认样式，然后网页开发者定义的样式又会覆盖用户样式。
>
> 再来看看优先级，从高到低依次为：网页开发者定义的样式、网页阅读者定义的样式、浏览器的默认样式。
>
> 对继承的元素来说，子元素自身的样式优先级高于从父级继承来的样式。
>
> > 更多细节   
> > CSS 另外提供了一个 !important 关键字，用户可以通过使用这个关键字使自己定义的样式覆盖掉开发者定义的样式。   
> > 这就意味着，作为开发者，你很难准确的预知页面最终在用户电脑上的显示效果。   

---

### 基于关系的选择器

选择器	|选择的元素
------- |  ---------
A E	|任何是元素A的后代元素E (后代节点指A的子节点，子节点的子节点，以此类推)
A > E	|任何元素A的子元素
E:first-child	|任何元素的第一个子元素E
B + E	|任何元素B的下一个兄弟元素E

---


### 例子

举一个作用域链的例子。

    var outVariable = "我是最外层变量"; //最外层变量
    function outFun() { //最外层函数
        var inVariable = "内层变量";
        function innerFun() { //内层函数
            console.log(inVariable);
            var tempVariable = inVariable;
        }
        innerFun();
    }

对最开始的代码稍加修改

其作用域链为：

    window
    ├──outVariable
    └──outFun()
       ├──inVariable
       └──innerFun()
          └──tempVariable

对于 `innerFun()`，其作用域链包含 3 个对象：innerFun() 自己的变量对象、outFun()的变量对象、全局变量对象。

---