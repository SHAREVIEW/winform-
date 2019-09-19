# winform-


在WinForm之间传值有很多种方法,在这里我用的是delegate and event进行传值.

新建一个WindowsApplication,创建两个WinForm.其实它们就是两个类.

每个WinForm中各加入一个Button和一个TextBox.

在WinForm2中写入代理和事件(delegate and event)如下:

//代理声明

public delegate void SendMessage(string str);

//事件声明

public event SendMessage SendEvent;

private void btnSend_Click(object sender, EventArgs e)

{
       //调用事件
       
      SendEvent(textBox1.Text);
      
}

在WinForm1中写入如下代码:

private void btnShow_Click(object sender, EventArgs e)

{

        Form2 f2 = new Form2();
        
        //Form2事件注册
        
        f2.SendEvent+=new Form2.SendMessage(GetMessage);
        
        f2.Show();
}

//代理调用的方法

public void GetMessage(string str)

{

       textBox1.Text = str;
       
}
