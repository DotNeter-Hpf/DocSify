
!> **Theme Studio for WinForms 可用于从现有主题为 Syncfusion 控件创建和应用新主题**

## 1.启动 Theme Studio

![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220627215939.png)

### 1.1 左侧主题自定义，右侧控件预览
**`左侧随意选择主题颜色，右侧呈现对应颜色的效果`**
![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220627220125.png)
 
 ### 1.2 Export 按需导出
 **`可以导出所有，或导出指定控件；减少最终输出组件的大小`**
![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220627220236.png)

**`导出文件为：VioletTheme.dll `**

## 2.代码中使用

程序集需要手动导入

### 2.1 Program中加载主题程序集
* 项目中引用 Syncfusion.Licensing.dll (可以NuGet下载)
* 项目引入 Export导出的dll

```csharp
static void Main()
        {
            Syncfusion.Licensing.SyncfusionLicenseProvider.RegisterLicense("YOUR LICENSE KEY");
            SkinManager.LoadAssembly(typeof(VioletTheme).Assembly);
            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            Application.Run(new Form1());
        }
```

### 2.2 控件 ThemeName 属性赋值

```csharp
public partial class Form1 : SfForm
    {
        public Form1()
        {
            InitializeComponent();

            buttonEdit1.ThemeName = "VioletTheme";
        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }
    }
```

**`效果图：`**
* 使用主题前：
![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220627220309.png)

* 使用主题后：
![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220627220334.png)


[📄文档参考：Theme Studio(主题)](https://help.syncfusion.com/windowsforms/theme-studio/theme-studio)


<div id="NavigateDiv">
<table style="border:none;">
    <tr style="border:none;">
    <td style="border:none;width:300px"><a style="color:var(--sidebarSublink);font-size:18px;" > 目录导航 </a></td>
    </tr>
    <tr style="border:none;">
    <td style="border:none;width:300px"><a style="color:var(--sidebarSublink)" href="/#/SyncFusion/Winform/ThemeStudio?id=_1启动-theme-studio" > 1.启动 Theme Studio </a></td>
    </tr>
      <tr style="border:none;">
    <td style="border:none;width:300px"><a style="color:var(--sidebarSublink)" href="/#/SyncFusion/Winform/ThemeStudio?id=_11-左侧主题自定义，右侧控件预览" > &emsp;1.1 左侧主题自定义，右侧控件预览 </a></td>
    </tr>
     <tr style="border:none;">
    <td style="border:none;width:300px"><a style="color:var(--sidebarSublink)" href="/#/SyncFusion/Winform/ThemeStudio?id=_12-export-按需导出" > &emsp;1.2 Export 按需导出 </a></td>
    </tr>
    <tr style="border:none;">
    <td style="border:none;width:300px"><a style="color:var(--sidebarSublink)" href="/#/SyncFusion/Winform/ThemeStudio?id=_2代码中使用" > 2.代码中使用 </a></td>
    </tr>
    <tr style="border:none;">
    <td style="border:none;width:300px"><a style="color:var(--sidebarSublink)" href="/#/SyncFusion/Winform/ThemeStudio?id=_21-program中加载主题程序集" > &emsp;2.1 Program中加载主题程序集 </a></td>
    </tr>
    <tr style="border:none;">
    <td style="border:none;width:300px"><a style="color:var(--sidebarSublink)" href="/#/SyncFusion/Winform/ThemeStudio?id=_22-控件-themename-属性赋值" > &emsp;2.2 控件 ThemeName 属性赋值 </a></td>
    </tr>
</table>
</div>
