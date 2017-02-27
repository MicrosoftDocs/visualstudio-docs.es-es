---
title: "Creaci&#243;n de una ventana de herramienta de instancias m&#250;ltiples | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "múltiples"
  - "ventanas de herramientas"
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Creaci&#243;n de una ventana de herramienta de instancias m&#250;ltiples
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede programar una ventana de herramientas para que varias instancias del mismo pueden estar abiertos simultáneamente. De forma predeterminada, las ventanas de herramientas pueden tener sólo una instancia abiertos.  
  
 Cuando se utiliza una ventana de herramientas de varias instancias, puede mostrar varias fuentes relacionadas de información al mismo tiempo. Por ejemplo, podría poner varias líneas <xref:System.Windows.Forms.TextBox> control en una ventana de herramientas de varias instancias de modo que varios fragmentos de código están disponibles al mismo tiempo durante una sesión de programación. También, por ejemplo, podría poner un <xref:System.Windows.Forms.DataGrid> cuadro y una lista desplegable de control en una ventana de herramientas de varias instancias para que pueden realizar el seguimiento simultáneamente varios orígenes de datos en tiempo real.  
  
## Creación de una ventana de herramientas Basic \(instancia única\)  
  
1.  Cree un proyecto denominado **MultiInstanceToolWindow** utilizando la plantilla VSIX y agregar una plantilla de elemento de ventana de herramientas personalizada denominada **MIToolWindow**.  
  
    > [!NOTE]
    >  Para obtener más información acerca de cómo crear una extensión con una ventana de herramientas, consulte [Crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Realizar una instancia múltiple de ventana de herramienta  
  
1.  Abra la **MIToolWindowPackage.cs** archivo y busque la `ProvideToolWindow` atributo. y el `MultiInstances=true` parámetro, como se muestra en el ejemplo siguiente.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  En el archivo MIToolWindowCommand.cs, busque el método ShowToolWindos\(\). En este método, llame a la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> \(método\) y establezca su `create` marca `false` por lo que creará una iteración a través de las instancias existentes de ventana de herramienta hasta disponible `id` se encuentra.  
  
3.  Para crear una instancia de la ventana de herramienta, llame a la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> \(método\) y establezca su `id` en un valor disponible y su `create` marca `true`.  
  
     De forma predeterminada, el valor de la `id` parámetro de la <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> método es `0`. Esto hace que una ventana de herramientas de instancia única. Para que alojar más de una instancia, cada instancia debe tener su propia `id`.  
  
4.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método en la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto devuelto por la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> propiedad de la instancia de la ventana de herramienta.  
  
5.  De forma predeterminada, la `ShowToolWindow` método creado por la plantilla de elemento de la ventana de herramienta crea una ventana de herramientas de instancia única. En el ejemplo siguiente se muestra cómo modificar el `ShowToolWindow` método para crear varias instancias.  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```