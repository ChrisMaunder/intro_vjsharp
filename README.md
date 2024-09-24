# Introduction to Visual J# .NET

An overview of the latest Java language tools from Microsoft.
<!-- Main HTML starts here -->

![](https://raw.githubusercontent.com/ChrisMaunder/intro_vjsharp/master/docs/assets/newproject.gif)

## Introduction

Microsoft have released a major piece of the 
JUMP initiative: Visual J# .NET. This is a set of new tools for those 
wishing to develop using the java-language syntax. "Java Language Syntax" is the 
important point here. It is not Java - it's J#. 

Visual J# .NET beta 1 can be downloaded from [here](http://msdn.microsoft.com/downloads/default.asp?URL=/downloads/sample.asp?url=/msdn-files/027/001/754/msdncompositedoc.xml).

![\]\(https://raw.githubusercontent.com/ChrisMaunder/intro_vjsharp/master/docs/assets/vjsharp.gif)Visual J# .NET beta 1 is fully integrated into Visual Studio .NET beta 2. It 
can be used to develop applications, class libraries and web services for .NET, 
and like other .NET languages targets the .NET CLR and uses the base class 
libraries. As well, J# includes features of other first class languages such as 
cross language integration, security, versioning and deployment, and debugging 
and profile support. The J# documentation notes that even if you do not have 
Visual J# .NET installed on your machine you can still debug your java-language 
applications.

The new tools include:

- the J# compiler to convert your java language source 
  code to MSIL
- A converter to convert java-language bytecode into 
  MSIL (*jbimp.exe*)
- Class libraries that provide some of the capabilities 
  of the JDK 1.1.4 packages that were included in Visual J++ 6.0
- WFC and many of the com.ms.\* packages (com.ms.lang, 
  com.ms.dll, com.ms.com, com.ms.win32)

Microsoft is making a very clear distinction between Java - the trademarked 
technology from Sun - and the java language syntax. Files containing the J# 
language will have the extension *.jsl.* This distinction is important 
because Visual J# .NET *does not* contain the following 
functionality:

- The ability to create .class bytecode files
- The ability to develop java applets for browsers
- The ability to create applications that will run in a 
  JVM.
- No support for the Java Native Interface or Remote 
  Method Invocation
- Support for the sun.io.\*, sun.net.\*, and netscape.\* packages

## Upgrading Visual J++ 6.0 projects.

To upgrade Visual J++ 6.0 projects to Visual J# .NET simply open the VJ++ 
project in the Visual Studio .NET IDE and you will be prompted to have the 
project upgraded. A new solution file (*.jshproj*) will be created for 
your J# project.

There are a couple of issues involved in upgrading such 
as no support for Pre and post build steps, and version information now being 
stored in an assembly, and the CLASSPATH feature of VJ++ 6.0 is not supported. 

## .NET stuff not supported by Visual J#

Java has been compared extensively to C#, but once you get past the familar 
syntax there are significant differences (see [A Comparative Overview of C#](http://genamics.com/developer/csharp_comparative.htm)). Visual J# does 
*not*  support the following features:

- Syntax support to define properties, events, value 
  types and delegates
- Syntax for consuming properties and events.
- Operator overloading
- Implicit and explicit conversions between types using 
  the op\_Implicit and op\_Explicit conversion operators.
- Seamless coercion between java-language data types and .NET Framework data 
  types.

## CodeDOM and Visual J#

Visual J# supports the .NET CodeDOM. CodeDOM, or Code Document Object Model, 
provides a way to describe the structure of a piece of source code that can 
be rendered in multiple languages. It's used in ASP.NET to render HTML pages, 
XML Web Service proxies, code wizards, designers etc, or for dynamic 
compilation.

## COM Interop and exposing J# components to COM

COM Interop is supported in much the same was as was done in Visual J++ 
(ie. using the JActiveX tool) and using J# components from unmanaged clients is 
achieved by using the RegAsm tool that ships with the .NET SDK. See the online 
docs for more information.

## Hello, World

![\]\(https://raw.githubusercontent.com/ChrisMaunder/intro_vjsharp/master/docs/assets/helloworld.GIF)

Obviously no introductory article on J# would be complete without HelloWorld.
The code is very similar to what you would write using either C# or VB.NET,
though there enough differences to make it clear that this is neither.

```java
package WindowsApplication1;

import System.Drawing.*;
import System.Collections.*;
import System.ComponentModel.*;
import System.Windows.Forms.*;
import System.Data.*;

//    Summary description for Form1.
public class Form1 extends System.Windows.Forms.Form
{
    private System.Windows.Forms.Button button1;
    //    Required designer variable.
    private System.ComponentModel.Container components = null;
    
    public Form1()
    {
        //
        // Required for Windows Form Designer support
        //
        InitializeComponent();
    
        //
        // TODO: Add any constructor code after InitializeComponent call
        //
    }
    
    // Clean up any resources being used.
    protected void Dispose(boolean disposing)
    {
        if (disposing)
        {
            if (components != null)
            {
                components.Dispose();
            }
        }
        super.Dispose(disposing);
    }

#region Windows Form Designer generated code
    //    Required method for Designer support - do not modify
    //    the contents of this method with the code editor.
    private void InitializeComponent()
    {
        this.button1 = new System.Windows.Forms.Button();
        this.SuspendLayout();
        // 
        // button1
        // 
        this.button1.set_Location(new System.Drawing.Point(((int)96), ((int)32)));
        this.button1.set_Name("button1");
        this.button1.set_TabIndex(((int)0));
        this.button1.set_Text("Click Me!");
        this.button1.add_Click( new System.EventHandler(this.button1_Click) );
        // 
        // Form1
        // 
        this.set_AutoScaleBaseSize(new System.Drawing.Size(((int)5), ((int)13)));
        this.set_ClientSize(new System.Drawing.Size(((int)272), ((int)93)));
        this.get_Controls().AddRange(new System.Windows.Forms.Control[] {this.button1});
        this.set_Name("Form1");
        this.set_Text("HelloWorld");
        this.ResumeLayout(false);
    
    }
#endregion
    
    // The main entry point for the application.
    /** @attribute System.STAThreadAttribute() */
    public static void main(String[] args) 
    {
        Application.Run(new Form1());
    }
    
    private void button1_Click (System.Object sender, System.EventArgs e)
    {
        System.Windows.Forms.MessageBox.Show("Hello, World!");
    }
}
```

## Visual J# .NET

![](https://raw.githubusercontent.com/ChrisMaunder/intro_vjsharp/master/docs/assets/jsharp.gif)

Visual J# .NET has been designed to allow developers to move from Visual J++ 
to J# as painlessly as possible. The documentation states "The only new syntax 
extensions are the keyword **ubyte** for consuming unsigned bytes and the 
**@attribute** directive, which can be used to attach custom attributes to 
the generated metadata."

Visual J# .NET allows developers to write fully managed .NET applications 
using the java language syntax, and to move their existing java language 
applications over to .NET, but is not, one would imagine, the language of choice 
when developing .NET applications. J# is RAD, is fully managed, and includes 
CodeDOM support making it suitable for ASP.NET and the designer (unlike the 
current incarnation of Managed C++) but it lacks support for important .NET 
features such as properties, value types, delegates and events (unlike MC++ and C#).

Even so, with .NET allowing inter-language operability and COM Interop, J# 
will allow Java developers wishing to move to .NET the ability to retain a good 
portion of their legacy java language code while moving forward with .NET 
development.
