# WPFWindowBase 使用教程

# 1 快速开始
#### 创建项目

1.打开VS，创建项目

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/image-20221112141309271.png" alt="image-20221112141309271" style="zoom:50%;" />



2.选择**WPF应用（.NET Framework）**

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/image-20221112141558450.png" alt="image-20221112141558450" style="zoom:50%;" />



3.选择**.Net Framework4.5**

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141719518.png" alt="image-20221112141701143" style="zoom:50%;" />



4. 创建好的项目

   <img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141726811.png" alt="image-20221112141819610" style="zoom:50%;" />



#### 类库安装

1. 配置单位Nuget地址，在Visual Studio的工具栏，打开“工具”-->“选项”。

   <img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141737350.png" alt="image-20221112142114597" style="zoom:50%;" />

2. 在左侧菜单，找到“Nuget包管理器”中“程序包源”中配置如下地址。

   <img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141739967.png" alt="image-20221112142243925" style="zoom:50%;" />

3. 点击确定后，右键项目，选择管理“管理Nuget程序包”

   <img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141739620.png" alt="image-20221112142345341" style="zoom:50%;" />

4. 在“Nuget程序包管理器”页面，切换到单位程序包源。

   <img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141742841.png" alt="image-20221112142530364" style="zoom:50%;" />

5. 选择“浏览”切页，在“搜索”输入框输入**“WPFWindowBase”**，选择最新版本安装。

   <img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141742970.png" alt="image-20221112142710487" style="zoom:50%;" />

6. 安装后，项目引用下有显示。

   <img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141742196.png" alt="image-20221112142835681" style="width:300px;height:400px;" />

   

#### 添加主题

1.双击“App.xml"文件，在输入如下代码，添加主体样式。

```xaml
<Application x:Class="WpfWindowBaseDemo.App"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:local="clr-namespace:WpfWindowBaseDemo"
             StartupUri="MainWindow.xaml">
    <Application.Resources>
        <ResourceDictionary Source="pack://application:,,,/WPFWIndowBase;component/Themes/BlueGradient/BlueGradientTheme.xaml"/>
    </Application.Resources>
</Application>
```

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141743491.png" alt="image-20221112143507160" style="zoom:50%;" />



#### 添加主界面

1.**\<Application\>**标记中的“StartupUri”属性指向的是启动界面。双击**“MainWindow.xaml”** 在**<Window>**标记下添加**WPFWindowBase**中的基础控件引用。

` xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase"`

2.修改**\<Window\> \</Window\>** 修改为**\<bc:WindowBaseEx\>...\</bc:WinodwBaseEx\>**。

3.在**\<bc:WindowBaseEx\>**中，添加主界面样式**`Style="{StaticResource WindowBaseStyleEx}"`**。

4.修改**MainWindow.xaml.cs**中的代码，使用**`using WPFWindowBase.BaseControl;`**引用**WPFWindowBase**库，将**Window**类修改为**WindowBaseEx**类。

5.在**\<bc:WindowBaseEx\>**标记中添加 Loaded事件**`Loaded="WindowBaseEx_Loaded"`**。并在Loaded事件处理方法中添加**`this.WindowMax();`**

6.完整**MainWindow.xaml**如下。

```xaml
<bc:WindowBaseEx x:Class="WpfWindowBaseDemo.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfWindowBaseDemo"
        xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800" Style="{StaticResource WindowBaseStyleEx}" Loaded="WindowBaseEx_Loaded"> 
    <Grid>
        
    </Grid>
</bc:WindowBaseEx>
```

7.完整的**MainWindow.xaml.cs**代码

```c#
using WPFWindowBase.BaseControl;

namespace WpfWindowBaseDemo
{
    public partial class MainWindow : WindowBaseEx
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void WindowBaseEx_Loaded(object sender, System.Windows.RoutedEventArgs e)
        {
            this.WindowMax();
        }
    }
}
```

8.启动项目。

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141743756.png" alt="image-20221112150024498" style="zoom:50%;" />



#### 添加子界面

1.右键项目，选择“新建文件夹”，命名为“**GetStarted**”。

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141744847.png" alt="image-20221112150324174" style="zoom:50%;" />

2.右键“**GetStarted**”文件夹，添加“**WPF窗口**”，命名为FirstUI。

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141744334.png" alt="image-20221112150501416" style="zoom:50%;" />

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141743075.png" alt="image-20221112150812528" style="zoom:50%;" />



3.双击“**FirstUI.xaml.cs**”，使用**`using WPFWindowBase.BaseControl;`**引用**WPFWindowBase**库，将**Window**类修改为**ChildBaseEx2**。

```C#
using WPFWindowBase.BaseControl;

namespace WpfWindowBaseDemo.GetStarted
{
    public partial class FirstUI : ChildBaseEx2
    {
        public FirstUI()
        {
            InitializeComponent();
        }
    }
}
```

4.双击“FirstUI.xaml”，添加如下代码，引用基础控件

` xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase"`

5.将**\<Window\> \</Window\>** 修改为**\<bc:ChildBaseEx2\>...\</bc:ChildBaseEx2\>**。并在**\<bc:ChildBaseEx\>**中

添加样式`Style="{StaticResource ChildBaseStyleEx2}"`，修改**Title**属性为**Caption**。

```xaml
<bc:ChildBaseEx2 x:Class="WpfWindowBaseDemo.GetStarted.FirstUI"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"        
        xmlns:local="clr-namespace:WpfWindowBaseDemo.GetStarted"
        xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase"
        mc:Ignorable="d"
       Caption="FirstUI" Height="450" Width="800" Style="{StaticResource ChildBaseStyleEx2}">
    <Grid>        
    </Grid>
</bc:ChildBaseEx2>
```

6.在FirstUI.xaml中添加如下代码，输出“我使用WPFWindowBase类库制作的第一个程序！”，并设置居中；

```xaml
<bc:ChildBaseEx2 x:Class="WpfWindowBaseDemo.GetStarted.FirstUI"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"        
        xmlns:local="clr-namespace:WpfWindowBaseDemo.GetStarted"
        xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase"
        mc:Ignorable="d"
       Caption="FirstUI" Height="450" Width="800" Style="{StaticResource ChildBaseStyleEx2}">
    <Grid>
        <TextBlock VerticalAlignment="Center"  HorizontalAlignment="Center" Text="我使用WPFWindowBase类库制作的第一个程序！" FontSize="24"/>
    </Grid>
</bc:ChildBaseEx2>
```

7.在MainWindow.xaml.cs中的Loaded事件中，添加如下代码。

```C#
private void WindowBaseEx_Loaded(object sender, System.Windows.RoutedEventArgs e)
{
    this.WindowMax();
    ChildBaseEx2.ShowWinodwFunc<FirstUI>();
}
```

#### demo展示

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141743509.png" alt="image-20221112152858902" style="zoom:50%;" />

**子界面拖动**，选择标题栏即可拖动。

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141743375.png" alt="image-20221112153022282" style="zoom:50%;" />

**子界面放大**，点击放大按钮

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141743109.png" alt="image-20221112153128131" style="zoom:50%;" />

**子界面缩小**，点击缩小按钮

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141743883.png" alt="image-20221112153156418" style="zoom:50%;" />

**子界面缩放**，点击子界面，按住**ctrl**键和**鼠标滚轮**即可。

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141745289.png" alt="image-20221112153341257" style="zoom:50%;" />



# 2 常用属性
## 2.1 控件属性

|          属性名称          |        属性说明        | 示例                               |
| :------------------------: | :--------------------: | :--------------------------------- |
|           Width            |          宽度          | Width="200"                        |
|           Height           |          高度          | Height="400"                       |
|          MaxWidth          |        最大宽度        | MaxWidth="500"                     |
|         MaxHeight          |        最大高度        | MaxHeight="600"                    |
|           Margin           | 外边距(左、上、右、下) | Margin="2,4,8,2"                   |
|          Padding           |         内边距         | Padding="3,3,3,3"                  |
|          FontSize          |        字体大小        | FontSize="14"                      |
|    HorizontalAlignment     |      控件水平对齐      | HorizontalAlignment="Left"         |
|     VerticalAlignment      |      控件垂直对齐      | VerticalAlignment="Center"         |
| HorizontalContentAlignment |    控件内容水平对齐    | HorizontalContentAlignment="Right" |
|  VerticalContentAlignment  |    控件内容垂直对齐    | VerticalContentAlignment="Top"     |

## 2.2 附加属性

|                   属性名称                   |         属性说明         | 示例                                                |
| :------------------------------------------: | :----------------------: | :-------------------------------------------------- |
|                   Grid.Row                   | 设置控件在Grid中在第几行 | Grid.Row=2                                          |
|                 Grid.Column                  | 设置控件在Grid中在第几列 | Grid.Column=5                                       |
|                 Grid.RowSpan                 | 设置控件在Grid中跨度多行 | Grid.RowSpan=3                                      |
|               Grid.ColumnSpan                | 设置控件在Grid中跨度多列 | Grid.ColumnSpan=4                                   |
|    VirtualizingPanel .VirtualizationMode     |      虚拟化模式设置      | VirtualizingPanel.VirtualizationMode  =Standard     |
| ScrollViewer  .HorizontalScrollBarVisibility |      水平滚动条显示      | ScrollViewer  .HorizontalScrollBarVisibility=Hidden |
|  ScrollViewer  .VerticalScrollBarVisibility  |        垂直滚动条        | ScrollViewer  .VerticalScrollBarVisibility=Visible  |

# 3 框架

## 3.1 主界面

区域

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141745871.png" alt="image-20221113120529832" style="zoom:50%;" />

| 区域名称 | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| 标题栏   | 显示软件Logo、标题和一些提示信息。                           |
| 标签栏   | 界面最大化或者最小化时显示标签，点击标签可以切换界面。       |
| 主操作区 | 界面在一般大小时，可在该区域拖动，放大时，界面的内容区会填充该界面。 |
| 菜单区   | 底部菜单栏，表示软件的各个功能，是打开子界面的入口。         |



## 3.2 菜单栏

​	使用 `xmlns:bv="clr-namespace:WPFWindowBase.BaseControl.ButtonView;assembly=WPFWindowBase"` 引用**ButtonView**，里面包含按钮控件，并在**\<bc:WindowBaseEx\>** 中的**MenuContent**中设置菜单内容。代码如下：

```xaml
<bc:WindowBaseEx x:Class="WpfWindowBaseDemo.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfWindowBaseDemo"
        xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase"
        xmlns:bv="clr-namespace:WPFWindowBase.BaseControl.ButtonView;assembly=WPFWindowBase"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800" Style="{StaticResource WindowBaseStyleEx}" Loaded="WindowBaseEx_Loaded">
    <bc:WindowBaseEx.MenuContent>
        <UniformGrid Name="UMenu" Background="White" Columns="5">
            <bv:MenuImgButton Name="MIB_Main" Style="{StaticResource MenuImgBtnStyle}"   Text="主界面" IsSelected="True"/>
            <bv:MenuImgButton Name="MIB_Simple" Style="{StaticResource MenuImgBtnStyle}"  Text="一般控件"/>
            <bv:MenuImgButton Name="MIB_Complex" Style="{StaticResource MenuImgBtnStyle}"  Text="复杂控件"/>
            <bv:MenuImgButton Name="MIB_DifficultPoint" Style="{StaticResource MenuImgBtnStyle}" Text="难点"/>
            <bv:MenuImgButton Name="MIB_ImportantExample" Style="{StaticResource MenuImgBtnStyle}" Text="重要案例"/>
        </UniformGrid>
    </bc:WindowBaseEx.MenuContent>
    <Grid>
      
    </Grid>
</bc:WindowBaseEx>
```

菜单效果：

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141745557.png" alt="image-20221113135030552" style="zoom:50%;" />



## 3.3 菜单页

接下来，我们为每一个菜单栏添加一个菜单页。

1.右键项目-->添加-->新建文件夹，命名为Pages。

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141745421.png" alt="image-20221113135315618" style="zoom:50%;" />

2.右键**”Pages“**-->添加-->用户控件，命名为PageMain。

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141745614.png" alt="image-20221113135559950" style="width: 600px; zoom: 50%;" />

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141745311.png" alt="image-20221113135759301" style="zoom:33%;" />

3. 双击**PageMain.xaml.cs**文件，进入代码，将**PageMain**的父类**UserControl**类为**PageBase**类。并在**PageMain.xaml**中通过

   `xmlns:bc ="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase"`

   引用基础控件。并将**\<UserControl\>** 修改**\<bc:PageBase\>**

4. 在**PageMain.xaml**中添加Load事件，并添加一个菜单页按钮，整体代码如下：

   ```xaml
   <bc:PageBase x:Class="WpfWindowBaseDemo.Pages.PageMain"
                xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:local="clr-namespace:WpfWindowBaseDemo.Pages"
                xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase" xmlns:wp="clr-namespace:WPFWindowBase.Page;assembly=WPFWindowBase" xmlns:bv="clr-namespace:WPFWindowBase.BaseControl.ButtonView;assembly=WPFWindowBase"
                mc:Ignorable="d" 
                d:DesignHeight="450" d:DesignWidth="800" Loaded="PageBase_Loaded">
    
       <UniformGrid Margin="70,30,70,30" Name="GContent" Columns="6" Rows="3" >
           <bv:ImgButtonEx Name="Btn_FirstUI" Margin="10,20,10,20" Text="FirstUI" Cursor="Hand"/>
       </UniformGrid>
   </bc:PageBase>
   
   ```

   

5. 为按钮添加一个单机事件。打开我们在第1节中的FirstUI窗体，代码如下：

   ```C#
   using System.Windows;
   using WPFWindowBase.BaseControl;
   using WpfWindowBaseDemo.GetStarted;
   
   namespace WpfWindowBaseDemo.Pages
   {
       public partial class PageMain : PageBase
       {
           public PageMain()
           {
               InitializeComponent();
           }
   
           private void PageBase_Loaded(object sender, System.Windows.RoutedEventArgs e)
           {
               this.Btn_FirstUI.Click += P_FirstUI_Click;
           }
   
           private void P_FirstUI_Click(object sender,RoutedEventArgs e)
           {
               ChildBaseEx2.ShowWinodwFunc<FirstUI>();
           }
       }
   }
    
   
   ```



6. 与**PageMain**一样，我们添加**PageSimple（一般控件）**、**PageComplex（复杂控件）**、**PageDifficultPoint（难点）**、**PageImportantExample（案例）**等页。代码如下：

   **PageSimple.xaml：**

   ```xaml
   <bc:PageBase x:Class="WpfWindowBaseDemo.Pages.PageSimple"
                xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:local="clr-namespace:WpfWindowBaseDemo.Pages"
                xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase" xmlns:wp="clr-namespace:WPFWindowBase.Page;assembly=WPFWindowBase" xmlns:bv="clr-namespace:WPFWindowBase.BaseControl.ButtonView;assembly=WPFWindowBase"
                mc:Ignorable="d" 
                d:DesignHeight="450" d:DesignWidth="800" Loaded="PageBase_Loaded">
       <UniformGrid Margin="70,30,70,30" Name="GContent" Columns="6" Rows="3">
           <bv:ImgButtonEx  Margin="10,20,10,20" Text="标签" Cursor="Hand"/>
       </UniformGrid>
   </bc:PageBase>
   
   ```

   **PageComplex.xaml:**

   ```xaml
   <bc:PageBase x:Class="WpfWindowBaseDemo.Pages.PageComplex"
                xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:local="clr-namespace:WpfWindowBaseDemo.Pages"
                xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase" xmlns:wp="clr-namespace:WPFWindowBase.Page;assembly=WPFWindowBase" xmlns:bv="clr-namespace:WPFWindowBase.BaseControl.ButtonView;assembly=WPFWindowBase"
                mc:Ignorable="d" 
                d:DesignHeight="450" d:DesignWidth="800" Loaded="PageBase_Loaded">
       <UniformGrid Margin="70,30,70,30" Name="GContent" Columns="6" Rows="3">
           <bv:ImgButtonEx  Margin="10,20,10,20" Text="树形控件"/>
   
       </UniformGrid>
   </bc:PageBase>
   ```

   **PageDifficultPoints.xaml:**

   ```xaml
   <bc:PageBase x:Class="WpfWindowBaseDemo.Pages.PageDifficultPoints"
                xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:local="clr-namespace:WpfWindowBaseDemo.Pages"
                xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase" xmlns:wp="clr-namespace:WPFWindowBase.Page;assembly=WPFWindowBase" xmlns:bv="clr-namespace:WPFWindowBase.BaseControl.ButtonView;assembly=WPFWindowBase"
                mc:Ignorable="d" 
                d:DesignHeight="450" d:DesignWidth="800" Loaded="PageBase_Loaded">
       <UniformGrid Margin="70,30,70,30" Name="GContent" Columns="6" Rows="3">
           <bv:ImgButtonEx  Margin="10,20,10,20" Text="布局" Cursor="Hand"/>
       </UniformGrid>
   </bc:PageBase>
   
   ```

   **PageImportantExample.xaml:**

   ```xaml
   <bc:PageBase x:Class="WpfWindowBaseDemo.Pages.PageImportantExample"
                xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:local="clr-namespace:WpfWindowBaseDemo.Pages"
                xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase" xmlns:wp="clr-namespace:WPFWindowBase.Page;assembly=WPFWindowBase" xmlns:bv="clr-namespace:WPFWindowBase.BaseControl.ButtonView;assembly=WPFWindowBase"
                mc:Ignorable="d" 
                d:DesignHeight="450" d:DesignWidth="800" Loaded="PageBase_Loaded">
       <UniformGrid Margin="70,30,70,30" Name="GContent" Columns="6" Rows="3">
           <bv:ImgButtonEx   Margin="10,20,10,20" Text="事件委托" Cursor="Hand"/>
       </UniformGrid>
   </bc:PageBase>
   
   ```

   

7. 在**MainWindow.xaml**中添加上述几个菜单页。代码如下：

   ```xaml
   <bc:WindowBaseEx x:Class="WpfWindowBaseDemo.MainWindow"
           xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
           xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
           xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
           xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
           xmlns:local="clr-namespace:WpfWindowBaseDemo"
           xmlns:bc="clr-namespace:WPFWindowBase.BaseControl;assembly=WPFWindowBase"
           xmlns:bv="clr-namespace:WPFWindowBase.BaseControl.ButtonView;assembly=WPFWindowBase" 
           xmlns:uipage="clr-namespace:WpfWindowBaseDemo.Pages"
                    mc:Ignorable="d"
           Title="MainWindow" Height="450" Width="800" ResizeMode="NoResize" WindowStyle="None" Style="{StaticResource WindowBaseStyleEx}"  VirtualizingPanel.VirtualizationMode="Recycling"  Loaded="WindowBaseEx_Loaded">
       <bc:WindowBaseEx.Background>
           <ImageBrush ImageSource="pack://application:,,,/WPFWindowBase;component/Resources/cc_bj.jpg" />
       </bc:WindowBaseEx.Background>
       <bc:WindowBaseEx.MenuContent>
           <UniformGrid Name="UMenu" Background="White" Columns="5">
               <bv:MenuImgButton Name="MIB_Main" Style="{StaticResource MenuImgBtnStyle}"   Text="主界面" IsSelected="True"/>
               <bv:MenuImgButton Name="MIB_Simple" Style="{StaticResource MenuImgBtnStyle}"  Text="一般控件"/>
               <bv:MenuImgButton Name="MIB_Complex" Style="{StaticResource MenuImgBtnStyle}"  Text="复杂控件"/>
               <bv:MenuImgButton Name="MIB_DifficultPoint" Style="{StaticResource MenuImgBtnStyle}" Text="难点"/>
               <bv:MenuImgButton Name="MIB_ImportantExample" Style="{StaticResource MenuImgBtnStyle}" Text="重要案例"/>
           </UniformGrid>
       </bc:WindowBaseEx.MenuContent>
       <Grid Name="GMain"  ClipToBounds="True" >
           <Canvas  x:Name="CMenu" Panel.ZIndex="-100"  Background="WhiteSmoke">
               <StackPanel x:Name="SPMenu" Canvas.Left="0" Canvas.Top="0" Width="5000" Orientation="Horizontal" >
                   <uipage:PageMain />
                   <uipage:PageSimple />
                   <uipage:PageComplex  />
                   <uipage:PageDifficultPoints  />
                   <uipage:PageImportantExample  />
               </StackPanel>
           </Canvas>
       </Grid>
   </bc:WindowBaseEx>
   
   ```

   

8. 在**MainWindow.xaml.cs**中添加点击菜单按钮，切换页面的算法。代码如下：

   ```C#
   using System;
   using System.Collections.Generic;
   using System.Windows;
   using System.Windows.Controls;
   using System.Windows.Media.Animation;
   using WPFWindowBase.BaseControl;
   using WPFWindowBase.BaseControl.ButtonView;
   using WpfWindowBaseDemo.GetStarted;
   
   namespace WpfWindowBaseDemo
   {
       public partial class MainWindow : WindowBaseEx
       {
           public MainWindow()
           {
               InitializeComponent();
               this.WindowState = WindowState.Maximized;
           }
   
           private void WindowBaseEx_Loaded(object sender, System.Windows.RoutedEventArgs e)
           {
               //ChildBaseEx2.ShowWinodwFunc<FirstUI>();         
               InitEvents();
               this.CMenu.Width = this.GMain.ActualWidth * SPMenu.Children.Count;
               this.CMenu.Height = this.GMain.ActualHeight;
               this.SPMenu.Width = this.CMenu.Width;
               this.SPMenu.Height = this.CMenu.Height;
               foreach (var item in this.SPMenu.Children)
               {
                   if (item is PageBase page)
                   {
                       page.Width = this.GMain.ActualWidth;
                   }
               }
           }
   
           private void SizeChangedHandler(object sender, SizeChangedEventArgs e)
           {
               SetMenuPage();
           }
   
           private void SetMenuPage()
           { 
               
           }
   
           private void InitEvents()
           {
               int i = 0;
               foreach(var item in UMenu.Children)
               {
                   if(item is MenuImgButton mb)
                   {
                       mb.Tag = i++;
                       mb.Click += (o, e) =>
                       {
                           PageTurning(mb);
                       };
                   }
               }
               this.SizeChanged += SizeChangedHandler;
           }
   
           int _currentPageIndex=0;
           private void PageTurning(MenuImgButton mb)
           {
               
               int index = Convert.ToInt32(mb.Tag);
               if (index < 0 || index > SPMenu.Children.Count - 1 || _currentPageIndex == index)
                   return; 
               PageBase p = SPMenu.Children[index] as PageBase;
               DoMove(Canvas.LeftProperty, -index * GMain.ActualWidth, 0.1, 0.3, 0.4);
               _currentPageIndex = index;
               for (int i = 0; i < UMenu.Children.Count; i++)
               {
                   MenuImgButton mib = UMenu.Children[i] as MenuImgButton;
                   if (i == _currentPageIndex)                
                       mib.IsSelected = true;
                   else
                       mib.IsSelected = false;
               }            
           }
   
           private void DoMove(DependencyProperty dp, double to, double ar, double dr, double duration)
           {
               DoubleAnimation doubleAnimation = new DoubleAnimation();//创建双精度动画对象  
   
               doubleAnimation.To = to;//设置动画的结束值  
               doubleAnimation.Duration = TimeSpan.FromSeconds(duration);//设置动画时间线长度  
               doubleAnimation.AccelerationRatio = ar;//动画加速  
               doubleAnimation.DecelerationRatio = dr;//动画减速  
               doubleAnimation.FillBehavior = FillBehavior.HoldEnd;//设置动画完成后执行的操作  
               SPMenu.BeginAnimation(dp, doubleAnimation);//设置动画应用的属性并启动动画  
           }
       }
   }
   
   ```

   

9. 启动项目：

   <img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141746975.png" alt="image-20221113210335391" style="zoom:50%;" />

   此时点击按钮可以切换页面。

   

## 3.4 子界面 

我们点击”主界面菜单“中的FirstUI按钮，即可打开我们在第一章中的页面。

<img src="https://raw.githubusercontent.com/eclipsexml/DocumentImage/main/img/202211141746374.png" alt="image-20221113210525549" style="zoom:50%;" />







常用属性

| 属性名称   | 说明 | 示例                                                         |
| ---------- | ---- | ------------------------------------------------------------ |
| Caption    | 标题 | Caption="第一个界面"                                         |
| IconSource | 图标 | IconSource="pack://application:,,,/WPFWindowBase;component/Resources/b日常业务-.png" |
|            |      |                                                              |



| 方法名称       | 说明                       | 示例               |
| -------------- | -------------------------- | ------------------ |
| ShowCB()       | 显示界面，作为普通界面显示 | cm.ShowCB();       |
| ShowCBDialog() | 显示界面，作为对话框显示   | cm.ShowCBDialog(); |
|                |                            |                    |



# 4 常用控件

## 4.1 标签

## 4.2 文本输入框

## 4.3 数字输入框
## 4.4 时间输入框
## 4.5 下拉选择框
## 4.6 按钮
## 4.7 树形控件
## 4.8 编辑表格
## 4.9 分页控件

## 4.10 复杂报表



# 4 要点
## 4.1 布局
## 4.2 绑定
## 4.3 虚拟化
## 4.4 多线程
## 4.5 转换器

# 5 案例说明
## 5.1 事件委托
## 5.2 联动绑定
## 5.3 MVVM通信
## ...









