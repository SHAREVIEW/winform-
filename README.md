# winform-


![](https://github.com/SHAREVIEW/winform-/blob/master/BD1C34AD-B9DC-4b08-9C07-4D94FED4E11E.png)
通过公共静态类进行传值；  
通过绑定事件进行传值；  
使用Attribute  
public partial class Form1 : Form  
  {  
  private void button1_Click(object sender, EventArgs e)  
  {  
  Form2 frm2 = new Form2();  
  frm2.Show(this);  
  }  
  }  
  public partial class Form2 : Form  
  {  
  private void button1_Click(object sender, EventArgs e)  
  {  
  Form1 frm1 = (Form1)this.Owner;  
  ((TextBox)frm1.Controls["textBox1"]).Text = this.textBox2.Text;  
  this.Close();  
  }  
  }  
还可使用委托
使用委托实现两个窗体的交互:
// 主窗体中
FromB frm = new FromB("Hello A");
frm.onReportProgress = new DoReportProgress(OnReportProgress);
frm.ShowDialog(); // 显示窗体
private void OnReportProgress(string str)
{
  MessageBox.Show(str);
}
// 子窗体
public delegate void DoReportProgress(string strInfor);
public DoReportProgress onReportProgress;
public FromB(string str) // 传入父窗体的值
{
  InitializeComponent();
  MessageBox.Show(str);
}
public void button1()
{
  if(onReportProgress!=null)
  onReportProgress("Hello B"); // 调用委托将值返回给父窗体
}
