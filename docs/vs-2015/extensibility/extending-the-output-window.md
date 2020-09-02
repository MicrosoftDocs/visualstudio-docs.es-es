---
title: Extender el Ventana de salida | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2788903c60564d501770616fbe3ad2335e60a250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204430"
---
# <a name="extending-the-output-window"></a>Ampliación de la ventana de salida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana de **salida** es un conjunto de paneles de texto de lectura y escritura. Visual Studio tiene estos paneles integrados: **compilar**, en el que los proyectos comunican mensajes sobre compilaciones y **General**, en el que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comunica mensajes sobre el IDE. Los proyectos obtienen una referencia al panel **compilar** automáticamente a través de los <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> métodos de interfaz y Visual Studio ofrece acceso directo al panel **General** a través del <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> servicio. Además de los paneles integrados, puede crear y administrar sus propios paneles personalizados.  
  
 Puede controlar la ventana de **salida** directamente a través de las <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces y. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz que ofrece el <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> servicio define los métodos para crear, recuperar y destruir los paneles de la ventana de **salida** . La <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz define los métodos para mostrar paneles, ocultar paneles y manipular el texto. Una manera alternativa de controlar la ventana de **salida** es a través de los <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> objetos y en el modelo de objetos de automatización de Visual Studio. Estos objetos encapsulan casi toda la funcionalidad de las <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaces y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . Además, los <xref:EnvDTE.OutputWindow> objetos y <xref:EnvDTE.OutputWindowPane> agregan cierta funcionalidad de nivel superior para facilitar la enumeración de los paneles de la ventana de **salida** y para recuperar el texto de los paneles.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Crear una extensión que usa el panel de salida  
 Puede crear una extensión que ejerza distintos aspectos del panel de salida.  
  
1. Cree un proyecto VSIX denominado `TestOutput` con un comando de menú llamado **TestOutput**. Para obtener más información, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Agregue las siguientes referencias:  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. En TestOutput.cs, agregue la siguiente instrucción using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4. En TestOutput.cs, elimine el método método ShowMessageBox. Agregue el siguiente código auxiliar de método:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5. En el constructor TestOutput, cambie el controlador de comandos a OutputCommandHandler. Esta es la parte que agrega los comandos:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6. Las secciones siguientes tienen distintos métodos que muestran distintas formas de tratar con el panel de salida. Puede llamar a estos métodos para el cuerpo del método OutputCommandHandler (). Por ejemplo, el código siguiente agrega el método CreatePane () que se proporciona en la sección siguiente.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Crear un Ventana de salida con IVsOutputWindow  
 En este ejemplo se muestra cómo crear un nuevo panel de ventana de **salida** mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el comando **invocar TestOutput** debería ver la ventana de **salida** con un encabezado que indica **Mostrar resultados desde: CreatedPane** y las palabras **este es el panel creado** en el panel.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Crear un Ventana de salida con OutputWindow  
 En este ejemplo se muestra cómo crear un panel de la ventana de **salida** mediante el <xref:EnvDTE.OutputWindow> objeto.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Aunque la <xref:EnvDTE.OutputWindowPanes> colección le permite recuperar un panel de la ventana de **salida** por su título, no se garantiza que los títulos de los paneles sean únicos. Si duda de la unicidad de un título, use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> método para recuperar el panel correcto por su GUID.  
  
 Si agrega este método a la extensión proporcionada en la sección anterior, al hacer clic en el comando **invocar TestOutput** debería ver la ventana de salida con un encabezado que indica **Mostrar resultados desde: DTEPane** y el **Panel palabras agregadas DTE** en el panel.  
  
## <a name="deleting-an-output-window"></a>Eliminar un Ventana de salida  
 En este ejemplo se muestra cómo eliminar un panel de la ventana de **salida** .  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el comando **invocar TestOutput** debería ver la ventana de salida con un encabezado que indica **Mostrar resultados desde: nuevo panel** y el **Panel palabras agregadas creadas** en el panel. Si vuelve a hacer clic en el comando **invocar TestOutput** , se elimina el panel.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Obtener el panel General del Ventana de salida  
 En este ejemplo se muestra cómo obtener el panel **General** integrado de la ventana de **salida** .  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Si agrega este método a la extensión proporcionada en la sección anterior, al hacer clic en el comando **invocar TestOutput** debería ver que la ventana de **salida** muestra el **Panel palabras encontradas** en el panel.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Obtener el panel compilar de la Ventana de salida  
 Este ejemplo muestra cómo buscar el panel compilar y escribir en él. Dado que el panel compilación no está activado de forma predeterminada, lo activa también.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```
