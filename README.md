hss-pushState
==========================

这是一个基于H5 pushState的demo,方便理解pushState

## 为什么使用

众所周知，Ajax可以实现页面的无刷新操作——优点；但是，也会造成另外的问题，无法前进与后退！曾几何时，Gmail似乎借助iframe搞定，如今，HTML5让事情变得如同过家家般简单。
当执行Ajax操作的时候，往浏览器history中塞入一个地址（使用pushState）（这是无刷新的）；于是，返回的时候，通过URL或其他传参，我们就可以还原到Ajax之前的模样。

## 如何使用

- HTML5引入了history.pushState()和history.replaceState()这两个方法，他们允许添加和修改history实体。同时，这些方法会和- window.onpostate事件一起工作.
- replaceState是替换当前的历史信息，pushState是添加一条新的历史记录
- 这两个方法有三个参数(state,title,url)；
    第一个参数是一个json格式的参数，他可以存储我们在当前历史以后会用到的数据,也可以传null；第二个官方的介绍是说页面的标题，不过暂时用不到，直接传null就可以了；第三个参数是当前历史的url,如果为null则表示当前历史的url和上一历史的url没发生变化
- 示例：history.pushState({name:”名字”},null,”?name=张三”)；

- 注意：
    1.使用这两个方法时并不会直接触发onpopstate，而是存储了历史记录后前进或后退才会会触发onpopstate事件

　　2.history.pushstate有安全限制，其中之一是不允许应用推动跨url-s历史起源；服务器ip的端口不同和直接在电脑本地运行的html都会报错：
    3.只是hash改变不会触发window.onpostate

## 官网API

请参考参考[mozillaHistory_API](https://developer.mozilla.org/zh-CN/docs/Web/API/History_API)一文


## demo使用

ora文件是原生方式改变页面的状态
根目录下index和pushState是H5方式记录浏览器历史状态
- 打开index.html
- 手动输入pushState.html并携带参数?state=bg-org或bg-blue
- 可以随意点击中间按钮
- 测试浏览器默认后退，前进按钮

## 相关引用
有时间可以自己写一个pjax的项目，它把pushState+AJAX进行封装，当你点击一个站内的链接的时候， 不是做页面跳转， 而是只是站内页面刷新。 这样的用户体验， 比起整个页面都闪一下来说， 好很多。 其中有一个很重要的组成部分， 这些网站的ajax刷新是支持浏览器历史的， 刷新页面的同时， 浏览器地址栏位上面的地址也是会更改， 用浏览器的回退功能也能够回退到上一个页面。具体有点多多可以自行搜索
