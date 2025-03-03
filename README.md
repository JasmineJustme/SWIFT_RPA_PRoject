# SWIFT_RPA_Project
*该文档基于宇洲师兄的学习文档基础上编写内容*  

For student of SWIFT who want to learn RPA  
提供给SWIFT想要学习RPA库大一大二的小朋友们  
以下是本文档基于的库：[RPA-Python](https://github.com/tebelorg/RPA-Python)
示例代码在此：[Code in detail](https://github.com/JasmineJustme/SWIFT_RPA_Project/blob/main/Code_in_detail.md)
## 一、简单了解：  
### 1.Rpa的主要理解  
通过`模拟人的操作`，让电脑以`非侵入式`的方式进行网页的访问，使用`程序视觉`或者网页的`元素位置`给程序赋予精准定位点击元素位置的方式。  
### 2.技术的优点  
* 能够以非侵入式的方式访问一些网站，相较于传统的爬虫，不容易被察觉
* 能够在爬取网页的同时，同步进行多项其他的任务
### 3.技术的痛点
* 难以克服面对同一ip多次访问的识别。（进行ip掩盖尝试？）
* 难以克服反爬预警。（当跳出验证码or其他验证服务的时候难以自动解决只能人工进行干预）   
***不过RPA在代替重复点击的工作面前仍有很大的操作性，在未解决上述痛点前，可关注该方面***
## 二、基础知识
### 1. RPA库的操作（详情请查看[RPA-Python](https://github.com/tebelorg/RPA-Python)）：  
#### 高频  
* **r.url([url])**
当有参时该操作将打开指定网址。当无参时该操作将返回当下程序瞄准页面的url
* **r.click([xpath/selector])**
点击目标位置，xpath与selector都可作为定位使用，（*没有了解过的话可以往下翻到定位知识处*）
* **r.read([xpath/selector])**
获取目标文字，返回其中的文字部分（？***不太确定是只返回a标签部分还是所有文字了，大家自己实践一下吧***）
* **r.type([xpath/selector])**
向目标位置键入文字或[enter]等
* **r.popup([url])**
去到浏览器中指定的打开页面。当进行点击操作后若打卡了新的标签页，需要使用该函数式的程序瞄准新的一页
* **r.init()**
整个程序最开始时需要进行初始化
#### 其他  
* **r.wait([seconds])**
等待制定秒数、一般用于等待页面加载完成
* **r.dom([js code])**
一些需要的操作`rpa库无响应`或者`rpa库无对应操作`，使用js代码执行。（如检测页面是否加载完成一进行下一步操作） 
* **r.count([xpath/selector])**
统计页面对应的元素数量，一般用于遍历该页面所有项。（如获取该页面有多少个岗位描述框）
***
### 2. 定位知识：  
* HTML  [b站上HTML的简单介绍](https://www.bilibili.com/video/BV1Wr4y1R7Bd/?spm_id_from=333.337.search-card.all.click&vd_source=84e916dab357de3703e75e5fd708d19a)  
  大概了解一下网页上的文字都是怎么排布成我们所看到的样子就OK了
* CSS selector [b站上CSS selector的简单介绍](https://www.bilibili.com/video/BV1et411K7RU/?spm_id_from=333.337.search-card.all.click&vd_source=84e916dab357de3703e75e5fd708d19a)  
  大概了解一下，能知道为什么我们右键复制的selector能定位到我们的目标位置就OK了
* XML（就让我们先略过一下吧......）  
***
### 3. 数据整理及存放：  
* pandas 
  用于处理数据，对生成的dataframe进行处理，常用函数有pd.read_excel()...
  该库包含许多强大功能的函数，大家可以自行去问deepseek等等大语言模型解决你的疑问
* numpy  
  用于向量矩阵之间的运算等，使用同上，自行AI，熟能生巧^_-*
* 正则表达式  
  在现实世界中，无论是从`网络上爬取下来的数据`或者是`业务人员提供的数据`，会存在许多的干扰项或者是存在输入错误等信息
  通过该库可以有效帮助我们获取目的信息

## 三、拓展应用（忽略先吧，凑合打着先的）：  
### 1. Tableau、Power BI  
### 2. 与大语言模型的结合  
  



