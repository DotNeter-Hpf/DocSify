## Card(卡片)
带有阴影效果的卡片样式

### 效果图

![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521003834.png) ![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521003859.png)

### 安装 MaterialDesignThemes

![](https://cdn.jsdelivr.net/gh/DotNeter-Hpf/Images/img/20220521003209.png)

### 修改App.xaml
  * `引入命名空间`
```csharp
xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
```
  * `Application.Resources内添加代码`
```sharp
<Application.Resources>
    <ResourceDictionary>
        <ResourceDictionary.MergedDictionaries>
            <materialDesign:BundledTheme
                BaseTheme="Light"
                PrimaryColor="DeepPurple"
                SecondaryColor="Lime" />
            <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" />
        </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
</Application.Resources>
```
  `注意：`
    * `NuGet引入的工具包 MaterialDesignThemes GitHub → Wiki菜单中的 Super Quick Start (超级快速入门)`
    * `BaseTheme 设置主题颜色 Light(亮的);Dark(黑色)`

### 单个Card

粘贴图片后，点击图片，属性 → 生成操作 改成 '资源'

```csharp
<Window
    x:Class="WpfApp1.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:local="clr-namespace:WpfApp1"
    xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    Title="MainWindow"
    Width="800"
    Height="450"
    mc:Ignorable="d">
    <Grid>
        <materialDesign:Card
            Width="420"
            Height="270"
            Margin="4,2,8,16">
            <Grid VerticalAlignment="Stretch">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="*" />
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="200" />
                    <ColumnDefinition Width="*" />
                </Grid.ColumnDefinitions>

                <Image
                    Grid.RowSpan="5"
                    VerticalAlignment="Stretch"
                    Source="./Contact.png"
                    Stretch="UniformToFill"
                    StretchDirection="Both" />

                <TextBlock
                    Grid.Column="1"
                    Margin="16,16,16,2"
                    Style="{StaticResource MaterialDesignHeadline5TextBlock}"
                    Text="Get In Touch" />

                <TextBlock
                    Grid.Row="1"
                    Grid.Column="1"
                    Margin="16,0,16,8"
                    VerticalAlignment="Center"
                    Foreground="{DynamicResource MaterialDesignBodyLight}"
                    Text="Say hello, make a feature request, or raise a bug through one of these channels:"
                    TextWrapping="Wrap" />

                <Border
                    Grid.Row="2"
                    Grid.Column="1"
                    Margin="0,8,0,0"
                    BorderBrush="{DynamicResource MaterialDesignDivider}"
                    BorderThickness="0,1,0,0">
                    <Grid Margin="8">
                        <Button
                            x:Name="GitHubButton"
                            HorizontalAlignment="Left"
                            Style="{StaticResource MaterialDesignFlatButton}">
                            <StackPanel Orientation="Horizontal">
                                <materialDesign:PackIcon Kind="Github" />
                                <TextBlock
                                    Margin="8,0,0,0"
                                    VerticalAlignment="Center"
                                    Text="GitHub" />
                            </StackPanel>
                        </Button>

                        <Button
                            x:Name="TwitterButton"
                            HorizontalAlignment="Right"
                            Style="{StaticResource MaterialDesignFlatButton}">
                            <StackPanel Orientation="Horizontal">
                                <materialDesign:PackIcon Kind="Twitter" />
                                <TextBlock
                                    Margin="8,0,0,0"
                                    VerticalAlignment="Center"
                                    Text="Twitter" />
                            </StackPanel>
                        </Button>
                    </Grid>
                </Border>

                <Border
                    Grid.Row="3"
                    Grid.Column="1"
                    BorderBrush="{DynamicResource MaterialDesignDivider}"
                    BorderThickness="0,1,0,0">
                    <Grid Margin="8">
                        <Button
                            x:Name="ChatButton"
                            HorizontalAlignment="Left"
                            Cursor="Hand"
                            Style="{StaticResource MaterialDesignFlatButton}">
                            <StackPanel Orientation="Horizontal">
                                <materialDesign:PackIcon Kind="Message" />
                                <TextBlock
                                    Margin="8,0,0,0"
                                    VerticalAlignment="Center"
                                    Text="Chat" />
                            </StackPanel>
                        </Button>

                        <Button
                            x:Name="EmailButton"
                            HorizontalAlignment="Right"
                            Style="{StaticResource MaterialDesignFlatButton}">
                            <StackPanel Orientation="Horizontal">
                                <materialDesign:PackIcon Kind="Email" />
                                <TextBlock
                                    Margin="8,0,0,0"
                                    VerticalAlignment="Center"
                                    Text="Email" />
                            </StackPanel>
                        </Button>
                    </Grid>
                </Border>
            </Grid>
        </materialDesign:Card>
    </Grid>
</Window>
```

### 数据模板
我使用的是Prism框架
将控件以及样式封装起来，做成模板，动态创建使用

`实体类：`
```csharp
public class CardDto : BindableBase
    {
        private string title;

        public string Title
        {
            get { return title; }
            set { title = value; RaisePropertyChanged(); }
        }

        private string content;

        public string Content
        {
            get { return content; }
            set { content = value; RaisePropertyChanged(); }
        }
    }
```

`MainViewModel：`
```csharp
public class MainViewModel : BindableBase
    {
        public MainViewModel()
        {
            CardDtos = new ObservableCollection<CardDto>();
            Add();
        }

        private ObservableCollection<CardDto> cardDtos;
        public ObservableCollection<CardDto> CardDtos
        {
            get { return cardDtos; }
            set
            {
                cardDtos = value;
                RaisePropertyChanged();
            }
        }

        void Add()
        {
            CardDtos.Add(new CardDto() { Title = "111", Content = "测试1下吧" });
            CardDtos.Add(new CardDto() { Title = "222", Content = "测试2下吧" });
            CardDtos.Add(new CardDto() { Title = "333", Content = "测试3下吧" });
        }
    }
```

`MainView.xaml：`
```csharp
<Window
    x:Class="WpfApp1.MainView"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:local="clr-namespace:WpfApp1"
    xmlns:materialDesign="http://materialdesigninxaml.net/winfx/xaml/themes"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:prism="http://prismlibrary.com/"
    Title="MainWindow"
    Width="1200"
    Height="800"
    prism:ViewModelLocator.AutoWireViewModel="True"
    mc:Ignorable="d">
    <Grid>
        <StackPanel Grid.Column="1">
            <ScrollViewer Width="500" Height="600">
                <ListBox x:Name="Lbx" ItemsSource="{Binding CardDtos}">
                    <ListBox.ItemTemplate>
                        <DataTemplate>
                            <materialDesign:Card
                                Width="300"
                                Height="170"
                                Margin="4,2,8,16">
                                <Grid VerticalAlignment="Stretch">
                                    <Grid.RowDefinitions>
                                        <RowDefinition Height="Auto" />
                                        <RowDefinition Height="*" />
                                    </Grid.RowDefinitions>
                                    <TextBlock
                                        Margin="16,16,16,2"
                                        Style="{StaticResource MaterialDesignHeadline5TextBlock}"
                                        Text="{Binding Title}" />
                                    <TextBlock
                                        Grid.Row="1"
                                        Margin="16,0,16,8"
                                        VerticalAlignment="Center"
                                        Foreground="{DynamicResource MaterialDesignBodyLight}"
                                        Text="{Binding Content}"
                                        TextWrapping="Wrap" />
                                </Grid>
                            </materialDesign:Card>
                        </DataTemplate>
                    </ListBox.ItemTemplate>
                </ListBox>
            </ScrollViewer>
        </StackPanel>
    </Grid>
</Window>
```