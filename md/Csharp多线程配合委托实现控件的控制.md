# CSharp 多线程配合委托实现控件的控制

> 作者：TangHanF（GuoFu）
>
> 日期：2018年7月6日
>
> 说明：转载请注明出处，谢谢！🤝
>
> 联系方式：guofu_gh@163.com

-----

# 前言

> ​	在C#的Winform开发过程中，很多时候需要用到多线程以加快处理速度，当然了，多线程需要根据情况合理使用才能体现出它的价值。期间对于新手来说常常会遇到跨线程调用控件所出现的错误，这里需要说明一下：
>
> ​	“Windows 窗体”使用单线程单元 (STA) 模型，因为“Windows 窗体”基于本机 Win32 窗口，而 Win32 窗口从本质上而言是单元线程。STA 模型意味着可以在任何线程上创建窗口，但窗口一旦创建后就不能切换线程，并且对它的所有函数调用都必须在其创建线程上发生。除了 Windows 窗体之外，.NET Framework 中的类使用自由线程模型。
>
> **	STA 模型要求需从控件的非创建线程调用的控件上的任何方法必须被封送到（在其上执行）该控件的创建线程**。基类 Control 为此目的提供了若干方法（Invoke、BeginInvoke 和 EndInvoke）。Invoke 生成同步方法调用；BeginInvoke 生成异步方法调用。     
>
> ​	Windows 窗体中的控件被绑定到特定的线程，不具备线程安全性。
>
> ​	因此，**如果从另一个线程调用控件的方法，那么必须使用控件的一个 Invoke 方法来将调用封送到适当的线程**

​	在此我将多线程处理UI控件的流程简单梳理一下。

# 1、声明委托

csharp
// 定一个委托，接受一个字符串参数，然后void
private delegate void ChangeLabelText(string msg);
```



# 2、创建线程、启动线程

csharp
Thread thread = new Thread(new ThreadStart(方法名));
thread.Start();
```

# 3、实例化委托（即将委托指向一个具体方法）

# 4、调用委托



# 具体代码

> 启动一个循环，每次循环将结果赋值给窗体上的Label标签，完成之后修改Label标签值为“完成”

可能新手开始会这么做：

csharp
private void button1_Click(object sender, EventArgs e)
{
	Thread thread = new Thread(new ThreadStart(Test));
	thread.Start();
}


public void Test()
{
	for (int i = 0; i < 1000; i++)
	{
		Console.WriteLine(i);
        label1.Text=i.toString();// 放心，此处会报错，不信尝试一下
	}
}
```

以上代码看似顺理成章，创建线程—启动线程—线程的方法进行循环，同时修改Label值，但是存在问题，正确的做法应该是：

csharp
// 声明委托
private delegate void ChangeLabelText(string msg);


private void button1_Click(object sender, EventArgs e)
{
	Thread thread = new Thread(new ThreadStart(Test));
	thread.Start();
}


public void ModifyLabel(string text)
{
	label1.Text = text;
}

public void Test()
{
    // 实例化委托，将委托与ModifyLabel方法绑定
	ChangeLabelText changeLabelText = ModifyLabel;
	for (int i = 0; i < 1000; i++)
	{
		Console.WriteLine(i);
        // 通过控件的Invoke调用委托
		label1.Invoke(changeLabelText, new object[] { i.ToString() });
	}
	label1.Invoke(changeLabelText, new object[] { "完成" });
}
```

