# random

# 使用lodop打印web网页文件

描述：
传统打印控件总是“页面看到什么才能打印什么”，缺乏灵活性，使打印略显呆板。而使用lodop则可以做到“只看想看的、打印想打的”，不仅开发人员可以自由设置打印输出内容，用户还可对打印内容进行一系列调整。

原因：正常来说，打印自己的网页是无法把样式打印出来的，因此使用lodop；

```
<!--1.使用<object>标签嵌入ActiveX控件：在表单源码中的<head></head>中嵌入lodop插件-->

<object id="LODOP_OB" classid="clsid:2105C259-1E0C-4534-8141-A753534CB4CA" width="0" height="0">
      <embed id="LODOP_EM" type="application/x-print-lodop" width="0" height="0" pluginspage="install_lodop32.exe"></embed>
 </object>
```

中间使用boostrap来布局：类似简历；


```
function CreatePrintPage()

{
//定义对象
	LODOP = getLodop(document.getElementById('LODOP_OB'), document.getElementById('LODOP_EM'));

	var strBodyStyle = "<head>" + document.getElementById("head1").innerHTML + "</head>";

	//这里的“yangshi"是样式表的ID，如  <style type="text/css" id="yangshi"></style> 样式表加载在头部head，

	var strFormHtml = strBodyStyle + "<body>" + document.getElementById("divdiv1").innerHTML + "</body>";

	//这里的”divdiv1“是标签的名称。

	LODOP.PRINT_INIT("模板");//打印主题

	LODOP.SET_PRINT_PAGESIZE(1, 0, 0, "A4"); //A4纸张纵向打印

	// LODOP.SET_PRINT_STYLE("FontSize", 9);//打印字体

	LODOP.ADD_PRINT_HTML("0%", "0%", "100%", "100%", strFormHtml);

	//四个数值分别表示Top,Left,Width,Height

};

```

```

CreatePrintPage();//启动打印

LODOP.PREVIEW(); //打印预览
```
