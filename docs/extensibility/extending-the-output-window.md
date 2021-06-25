---
title: Extender el Ventana de salida | Microsoft Docs
description: Aprenda a ampliar la ventana Salida en el SDK Visual Studio y a crear y administrar sus propios paneles personalizados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 402c53691525530171edafd6a0751dfc72c9798d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900234"
---
# <a name="extend-the-output-window"></a>Extensión de la ventana Salida
La **ventana** Salida es un conjunto de paneles de texto de lectura y escritura. Visual Studio tiene estos paneles integrados: **Compilación**, en el que los proyectos comunican mensajes sobre compilaciones, y **General**, en los que comunica mensajes sobre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el IDE. Los proyectos obtienen una referencia al panel **Compilar** automáticamente a través de los métodos de interfaz y Visual Studio acceso directo al panel General a través <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> del  <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> servicio. Además de los paneles integrados, puede crear y administrar sus propios paneles personalizados.

 Puede controlar la ventana **Salida** directamente a través de las <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces y . La interfaz, que ofrece el servicio , define métodos para crear, recuperar y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> destruir paneles de <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> **ventana** de salida. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaz define métodos para mostrar paneles, ocultar paneles y manipular su texto. Una manera alternativa de controlar la **ventana Salida** es a través de los objetos y en el Visual Studio de objetos <xref:EnvDTE.OutputWindow> de <xref:EnvDTE.OutputWindowPane> Automation. Estos objetos encapsulan casi toda la funcionalidad de las <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces y . Además, los objetos y agregan alguna funcionalidad de nivel superior para facilitar la enumeración de los paneles de la ventana Salida y la recuperación de texto <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> de los paneles. 

## <a name="create-an-extension-that-uses-the-output-pane"></a>Creación de una extensión que use el panel Salida
 Puede crear una extensión que ejecte distintos aspectos del panel Salida.

1. Cree un proyecto VSIX denominado `TestOutput` con un comando de menú denominado **TestOutput**. Para obtener más información, vea [Crear una extensión con un comando de menú.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Agregue las siguientes referencias:

    1. EnvDTE

    2. EnvDTE80

3. En *TestOutput.cs,* agregue la siguiente instrucción using:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. En *TestOutput.cs,* elimine el `ShowMessageBox` método . Agregue el siguiente código auxiliar de método:

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

6. Las secciones siguientes tienen distintos métodos que muestran distintas formas de trabajar con el panel Salida. Puede llamar a estos métodos en el cuerpo del `OutputCommandHandler()` método. Por ejemplo, el código siguiente agrega el `CreatePane()` método dado en la sección siguiente.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Creación de una ventana de salida con IVsOutputWindow
 En este ejemplo se muestra cómo crear un nuevo panel **de ventana** salida mediante la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz .

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

 Si agrega este método a la extensión dada en la sección anterior, al hacer  clic en el comando **Invoke TestOutput** debería  ver la ventana Salida con un encabezado que dice Mostrar salida **de: CreatedPane** y las palabras Este es el panel creado en el propio panel.

## <a name="create-an-output-window-with-outputwindow"></a>Creación de una ventana de salida con OutputWindow
 En este ejemplo se muestra cómo crear un **panel de ventana** de salida mediante el objeto <xref:EnvDTE.OutputWindow> .

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
        panes.Add(title);
    }
}
```

 Aunque la colección le permite recuperar un panel de la ventana Salida por su título, no se garantiza que los títulos del panel <xref:EnvDTE.OutputWindowPanes> sean únicos.  Si duda de la unidad de un título, use el método para recuperar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> panel correcto por su GUID.

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el comando **Invoke TestOutput** debería ver la ventana Salida con un encabezado que dice Mostrar salida **de: DTEPane** y las palabras Panel **DTE** agregado en el propio panel.

## <a name="delete-an-output-window"></a>Eliminar una ventana de salida
 En este ejemplo se muestra cómo eliminar un **panel de la ventana** Salida.

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

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el comando **Invoke TestOutput** debería  ver la ventana Salida con un encabezado que dice Mostrar salida **de:** Nuevo panel y las palabras Panel creado agregado en el propio panel. Si vuelve a hacer clic **en el comando Invoke TestOutput,** se elimina el panel.

## <a name="get-the-general-pane-of-the-output-window"></a>Obtener el panel General de la ventana Salida
 En este ejemplo se muestra cómo obtener el panel **General integrado** de la **ventana** Salida.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Si agrega este método a la extensión dada en la sección anterior, al hacer  clic en el comando **Invoke TestOutput** debería ver que la ventana Salida muestra las palabras Panel **General** encontrado en el panel.

## <a name="get-the-build-pane-of-the-output-window"></a>Obtener el panel Compilación de la ventana Salida
 En este ejemplo se muestra cómo buscar el **panel Compilar** y escribir en él. Puesto que **el panel** Compilación no está activado de forma predeterminada, también lo activa.

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
