<div align="center">

## Using Parameters


</div>

### Description

Description: This is a simple java applet that shows how to get parameters from the html file and use them inside java. Remember Java is case sensitive, so the names in the html file must match your getParameter() names. Ex. html-PARAM NAME=Text Java-getParameter("Text"). It also shows how to convert hex color inputs to RGB color to use in Java.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Randy McCleary](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/randy-mccleary.md)
**Level**          |Intermediate
**User Rating**    |5.0 (25 globes from 5 users)
**Compatibility**  |Java \(JDK 1\.2\)
**Category**       |[Input/ Output](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/input-output__2-84.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/randy-mccleary-using-parameters__2-2533/archive/master.zip)

### API Declarations

<HTML>
<HEAD>
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=windows-1252">
<TITLE>
HTML Test Page
</TITLE>
</HEAD>
&lt;body>
<APPLET CODEBASE="myclasses" CODE="parameters.class" WIDTH=400 HEIGHT=300 HSPACE=0 VSPACE=0 ALIGN=middle>
 <PARAM NAME=Text VALUE="This is sample text.">
 <PARAM NAME=FontName VALUE="Courier">
 <PARAM NAME=FontStyle VALUE="1">
 <PARAM NAME=FontSize VALUE="20">
 <PARAM NAME=bgColor VALUE="CCCCCC">
 <PARAM NAME=fontColor VALUE="FF0000">
</APPLET>
</BODY>
</HTML>


### Source Code

```
//************************************************
//Author: Randy McCleary
//File Name: parameters.java
//Program: How to understand parameters.
//Description: This is a simple java applet that
// shows how to get parameters from the html file
// and use them inside java. Remember Java is
// case sensitive, so the names in the html file
// must match your getParameter() names. Ex.
// html-PARAM NAME=Text Java-getParameter("Text").
// It also shows how to convert hex color inputs
// to RGB color to use in Java.
//***********************************************
package parameters;
import java.awt.*;
import java.awt.event.*;
import java.applet.*;
import javax.swing.*;
import java.awt.color.*;
import java.awt.FlowLayout;
import java.awt.Label.*;
public class parameters extends Applet
{
	String text1;
	String text2;
	String text3;
	String text4;
	String text5;
	String fontName;
	int bgColorIndex;
	int fontColorIndex;
	int fontSize;
	int fontStyle;
	Color bgColor;
	Color fontColor;
	Font newFont1;
	Font newFont2;
	Font newFont3;
	Font newFont4;
	Font newFont5;
	FontMetrics fontMetrics;
	Graphics offbuff;
	Label output;
	public void init()
	{
	 //Get "Text" input parameter from html file.
	 //Get "fontName" parameter from html file
	 text1 = getParameter("Text1");
	 text2 = getParameter("Text2");
	 text3 = getParameter("Text3");
	 text4 = getParameter("Text4");
	 text5 = getParameter("Text5");
	 fontName = getParameter("FontName");
	 //Get fontStyle value. Values range from 0-3
	 //Style Values- Plain=0 Bold=1 Italic=2
	 //Bold&Italic=3
	 fontStyle = Integer.valueOf(getParameter("FontStyle")).intValue();
	 //Get fontSize value from parameter list.
	 fontSize = Integer.valueOf(getParameter("FontSize")).intValue();
	 //Create the new font thats going to be used.
	 newFont = new Font(fontName, fontStyle, fontSize);
	 fontMetrics = getFontMetrics(newFont);
	 //Get bgcolor parameter from html file
	 //Then convert it from hex to integer "FFFFFF - RGB"
	 //The 1st 2 FF's is the Red
	 //The 2nd 2 FF's is the Green
	 //The 3rd 2 FF's is the Blue
	 //FF = 16^2 - 1 = 255
	 //So FFFFFF is equal to 255,255,255
	 bgColorIndex = Integer.parseInt(getParameter("bgColor"), 16);
	 bgColor = new Color(bgColorIndex);
	 fontColorIndex = Integer.parseInt(getParameter("fontColor"), 16);
	 fontColor = new Color(fontColorIndex);
	 //Set the bgcolor and fontcolor to the RGB color just created
	 setBackground(bgColor);
	 setForeground(fontColor);
	 //Define what type of layout you would like to use
	 //This is in the Swing library.
	 setLayout(new FlowLayout(FlowLayout.CENTER));
	 //Put the input text on a label then set the
	 //font on the label created.
	 output = new Label(text1);
	 output.setFont(newFont1);
	 output = new Label(text2);
	 output.setFont(newFont2);
	 output = new Label(text3);
	 output.setFont(newFont3);
	 output = new Label(text4);
	 output.setFont(newFont4);
	 output = new Label(text5);
	 output.setFont(newFont5);
	 //Adds the label to display on the applet.
	 add(output);
	}
	public parameters()
	{
		fontName = "Arial";
	}
}
```

