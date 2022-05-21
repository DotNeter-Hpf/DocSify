## 创建Prism

Prism是一个用于WPF、Xamarin Form、Uno平台和 WinUI 中构建松散耦合、可维护和可测试的XAML应用程序框架

`通过以下方式访问、使用、学习它：`
>https://github.com/PrismLibrary/Prism
>https://github.com/PrismLibrary/Prism-Samples-Wpf
>https://www.nuget.org/packages/Prism.DryIoc/
>Visual Studio Extension：Prism Template Pack

### 1.1 通过Wpf模板创建

Visual Studio → 创建新项目 → Prism Blank App(WPF)

#### 1.1.1 添加Prism.DryIoc包

![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521231607.png)

![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521231641.png)

#### 1.1.2 修改App的基类

* **App.xaml.cs，将原有的基类 Application 替换成 PrismApplication**
 
![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521231709.png)

* **App.xaml，引入Prism命名空间，修改类名**
 
![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521231734.png)

* **重新生成解决方案，App.xaml.cs 鼠标放到App类名上，Alt+Enter 实现抽象类**
 
![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521231805.png)

* **App.xaml  文件下，将StartUri 属性删除，否则会启动两个页面**
 
![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521231907.png)


### 1.2 通过Prism模板创建

**Visual Studio → 创建新项目 → WPF 应用程序**

#### 1.2.1 添加扩展

**扩展 → 管理扩展 → Prism Template Pack**

![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521231940.png)

#### 1.2.2 创建基于Prism的空白模板

![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521232220.png)

![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521232245.png)


!> **按以上两种操作方式，创建的Prism模板都是一样的**

## 测试标题2

## 测试标题3

### 测试标题4

#### 测试标题5

##### 测试标题6