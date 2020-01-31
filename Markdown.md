# Markdown基本语法
## 标题 （#）：
- 几个#就是几级标题
## 列表（-+*）：
1. 有序列表（数字加点）
2. 无序列表（-*+ 跟内容之间都要有一个空格）
## 引用（>）：引用的文字前加>即可。引用也可以嵌套。
>这是个引用
>>这是个引用
>>>这是个引用
## 粗体（**加粗内容**）：
**要加粗的文字左右分别用两个*号包起来**
## 斜体（*要倾斜内容*）：
*要倾斜的文字左右分别用一个`*`号包起来*

## 图片alt
![这是张图片](./img/timg.jpg "这是张图片")

- 图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
- 图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加

## 超链接
[我的博客](https://alex-join.github.io/ "我的博客")  
- title可加可不加

## 单行代码：代码之间分别用一个反引号包起来
- 代码内容
   `this is code`

## 代码块：代码之间分别用三个反引号包起来，且两边的反引号单独占一行
- 代码内容 
```
    	<!--top-->
    	<nav class="navbar navbar-inverse navbar-fixed-top">
		  <div class="container-fluid">
		    <!-- Brand and toggle get grouped for better mobile display -->
		    <div class="navbar-header">
		      <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
		        <span class="sr-only">Toggle navigation</span>
		        <span class="icon-bar"></span>
		        <span class="icon-bar"></span>
		        <span class="icon-bar"></span>
		      </button>
		      <a class="navbar-brand" href="index.html">Alex的个人博客</a>
		    </div>
		    <!-- Collect the nav links, forms, and other content for toggling -->
		    <div class="collapse navbar-collapse navbar-right" id="bs-example-navbar-collapse-1">
		      <ul class="nav navbar-nav">
		        <li class="active"><a href="index.html">首页<span class="sr-only">(current)</span></a></li>
		        <li><a href="#">随笔</a></li>
		        <li><a href="#">笔记</a></li>
		        <li><a href="#">项目</a></li>
		      </ul>
		      <form class="navbar-form navbar-right">
			        <div class="form-group">
			          <input type="text" class="form-control" placeholder="搜索">
			        </div>
			        <button type="submit" class="btn btn-default">搜索</button>
		     	</form>
		    </div><!-- /.navbar-collapse -->
		  </div><!-- /.container-fluid -->
		</nav>
	<!--top-->
```

# jekyll的安装
1. 先安装 ruby，为了得到gem包管理工具
```
//查看是否安装成功，在cmd运行以下命令：
> gem -v
3.0.3
```
2. 开始安装jekyll
```
> gem install jekyll  //等着就行了

//查看是否安装成功
> jekyll -v
jekyll 4.0.0
```
---
hehe: 么么哒~
title: 我的第一篇博客
zhaiyao: 123456789
age: 18岁
aa: 12312132121
---
# Jekyll笔记
# 输出
用 `{{}}` 进行输出，如
<h1>name: {{page.name}}</h1>

# 过滤器
对内容进行过滤。
## 格式
```
{{page.aa | truncate:5,"*"}}

```
## 常见的过滤器
- truncate - 截取指定长度的字符串，第2个参数追加到字符串的尾部  
{{ 'foobarfoobar' | truncate: 5, '.' }} # => 'foob.'
- strip_html - 删除 HTML 标签  
{{ '<a href="">123</a>' }}
{{ '<a href="">123</a>' | strip_html }}
<br>
- 请参考： http://ju.outofmemory.cn/entry/149459
- 百度： jekyll语法 -> 第一条

# 全局变量
- page 代表当前页面，可以获取当前页面中定义的数据
- site 用于获取 `_config.yml` 配置文件中的数据
- content 用在模板文件中，代表子节点的内容
- paginator 获取分页的内容


# 目录结构
- _config.yml 文件，配置文件，在这个文件中配置的内容可以通过`site`全局变量获取
- _includes 文件夹 ，用于放置include包含的文件

#提取公共部分
1、include包含方式
>1、用`{% include 文件路径 %}` 包含文件
>2. 会去网站根目录下的 _includes 寻找相应文件

2. layouts布局方式
>1. 在网站根目录兴建 _layouts 文件夹
>2. 搞一个基本模板，将每个页面不同内容替换成`{{content}}`
>3. 在子模版中继承基本模板