---
title: Ampliación de la ventana de salida ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711644"
---
# <a name="extend-the-output-window"></a>Ampliar la ventana Salida
La ventana **Salida** es un conjunto de paneles de texto de lectura y escritura. Visual Studio tiene estos paneles integrados: **Compilar**, en el que los [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyectos comunican mensajes sobre compilaciones y **General**, en los que se comunican mensajes sobre el IDE. Los proyectos obtienen **Build** una referencia <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> al panel Compilar automáticamente a través de <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> los métodos de interfaz y Visual Studio ofrece acceso directo al panel **General** a través del servicio. Además de los paneles integrados, puede crear y administrar sus propios paneles personalizados.

 Puede controlar **Output** la ventana Salida <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> directamente a través de las interfaces y. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz, que <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> ofrece el servicio, define métodos para crear, recuperar y destruir paneles de ventana de **salida.** La <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaz define métodos para mostrar paneles, ocultar paneles y manipular su texto. Una forma alternativa de **Output** controlar el <xref:EnvDTE.OutputWindow> salida <xref:EnvDTE.OutputWindowPane> ventana es a través de la y objetos en el modelo de objetos de automatización de Visual Studio. Estos objetos encapsulan casi toda <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> la funcionalidad de las interfaces. Además, <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> los objetos y agregan alguna funcionalidad de nivel superior para facilitar la enumeración de los paneles de la ventana **Salida** y la recuperación de texto de los paneles.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Cree una extensión que use el panel Salida
 Puede crear una extensión que ejerza diferentes aspectos del panel Salida.

1. Cree un proyecto `TestOutput` VSIX denominado con un comando de menú denominado **TestOutput**. Para obtener más información, consulte [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Agregue las siguientes referencias:

    1. EnvDTE

    2. EnvDTE80

3. En *TestOutput.cs*, agregue la siguiente instrucción using:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. En *TestOutput.cs*, `ShowMessageBox` elimine el método. Agregue el siguiente código auxiliar de método:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. En el TestOutput constructor, cambie el controlador de comandos a OutputCommandHandler. Aquí está la parte que agrega los comandos:

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

6. Las secciones siguientes tienen diferentes métodos que muestran diferentes formas de tratar con el panel Salida. Puede llamar a estos métodos al cuerpo del `OutputCommandHandler()` método. Por ejemplo, el código `CreatePane()` siguiente agrega el método especificado en la sección siguiente.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Crear una ventana de salida con IVsOutputWindow
 En este ejemplo se muestra cómo crear <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> un nuevo panel de ventana de **salida** mediante la interfaz.

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

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el comando **Invocar TestOutput** debería ver la ventana **Salida** con un encabezado que dice **Mostrar salida desde: CreatedPane** y las palabras **Este es el panel Creado** en el propio panel.

## <a name="create-an-output-window-with-outputwindow"></a>Crear una ventana de salida con OutputWindow
 En este ejemplo se **Output** muestra cómo crear <xref:EnvDTE.OutputWindow> un panel de ventana Salida mediante el objeto.

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

 Aunque <xref:EnvDTE.OutputWindowPanes> la colección le permite recuperar un panel de la ventana **Salida** por su título, no se garantiza que los títulos del panel sean únicos. Cuando dude de la unicidad <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> de un título, use el método para recuperar el panel correcto por su GUID.

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el comando **Invocar TestOutput** debería ver la ventana Salida con un encabezado que dice **Mostrar salida desde: DTEPane** y las palabras **Añadido panel DTE** en el propio panel.

## <a name="delete-an-output-window"></a>Eliminar una ventana de salida
 En este ejemplo se muestra cómo eliminar un panel de ventana **Salida.**

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

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el comando **Invocar TestOutput** debería ver la ventana Salida con un encabezado que dice **Mostrar salida desde: Nuevo panel** y las palabras Añadido panel **creado** en el propio panel. Si vuelve a hacer clic en el comando **Invocar TestOutput,** se eliminará el panel.

## <a name="get-the-general-pane-of-the-output-window"></a>Obtenga el panel General de la ventana Salida
 En este ejemplo se muestra cómo obtener el panel **General** integrado de la ventana **Salida.**

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el comando **Invocar TestOutput** debería ver que la ventana **Salida** muestra las palabras del panel **General encontrado** en el panel.

## <a name="get-the-build-pane-of-the-output-window"></a>Obtenga el panel Compilar de la ventana Salida
 En este ejemplo se muestra cómo buscar el panel **Compilar** y escribir en él. Dado que el panel **Compilar** no está activado de forma predeterminada, también lo activa.

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
