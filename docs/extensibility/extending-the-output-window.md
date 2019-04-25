---
title: Extender la ventana de salida | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86498adc4d8bce2a7d428b2951764e5d4b8a96a9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041085"
---
# <a name="extend-the-output-window"></a>Ampliar la ventana de salida
El **salida** ventana es un conjunto de paneles de texto de lectura/escritura. Visual Studio tiene estos paneles integrados: **Compilar**, en los proyectos que se comunican los mensajes sobre las compilaciones, y **General**, en el que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comunica mensajes de información sobre el IDE. Proyectos de obtención una referencia a la **compilar** automáticamente a través del panel la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> métodos de interfaz y Visual Studio ofrece acceso directo a la **General** panel a través de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> servicio. Además de los paneles integrados, puede crear y administrar sus propios paneles personalizados.

 Puede controlar la **salida** directamente a través de la ventana la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz, que ofrece el <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> de servicio, que define los métodos para crear, recuperar y destruir **salida** paneles de ventana. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaz define métodos para mostrar paneles, ocultar paneles y manipular el texto. Una manera alternativa de controlar la **salida** ventana es a través de la <xref:EnvDTE.OutputWindow> y <xref:EnvDTE.OutputWindowPane> objetos en el modelo de objetos de automatización de Visual Studio. Estos objetos casi toda la funcionalidad de encapsulan la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces. Además, el <xref:EnvDTE.OutputWindow> y <xref:EnvDTE.OutputWindowPane> objetos agregan algunas funciones de nivel superior para que sea más fácil enumerar los **salida** paneles de ventana y para recuperar el texto de los paneles.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Crear una extensión que usa el panel de resultados
 Puede realizar una extensión que ejerce distintos aspectos del panel de salida.

1. Cree un proyecto VSIX denominado `TestOutput` con un comando de menú denominado **TestOutput**. Para obtener más información, consulte [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Agregue las siguientes referencias:

    1. EnvDTE

    2. EnvDTE80

3. En *TestOutput.cs*, agregue la siguiente instrucción using:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. En *TestOutput.cs*, elimine el `ShowMessageBox` método. Agregue el código auxiliar del método siguiente:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. En el constructor TestOutput, cambie el controlador de comandos a OutputCommandHandler. Aquí está lo que agrega los comandos:

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

6. Las secciones siguientes tienen métodos diferentes que muestran distintas formas de trabajar con el panel de salida. Puede llamar a estos métodos al cuerpo de la `OutputCommandHandler()` método. Por ejemplo, el código siguiente agrega el `CreatePane()` método indicado en la sección siguiente.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Creación de una ventana de salida con IVsOutputWindow
 En este ejemplo se muestra cómo crear un nuevo **salida** panel de ventana mediante el uso de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interfaz.

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

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el **invocar TestOutput** comando debería ver el **salida** ventana con un encabezado que dice **mostrar salida De: CreatedPane** y las palabras **este es el panel creado** en el propio panel.

## <a name="create-an-output-window-with-outputwindow"></a>Creación de una ventana de salida con OutputWindow
 En este ejemplo se muestra cómo crear un **salida** panel de ventana utilizando la <xref:EnvDTE.OutputWindow> objeto.

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

 Aunque el <xref:EnvDTE.OutputWindowPanes> colección le permite recuperar un **salida** panel de ventana por su título, los títulos del panel no se garantiza que sea único. Si tiene dudas acerca la exclusividad de un título, utilice el <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> método para recuperar el panel correcto por su GUID.

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el **invocar TestOutput** debería ver la ventana de salida con un encabezado que indica que el comando **mostrar resultados desde: DTEPane** y las palabras **agregado DTE panel** en el propio panel.

## <a name="delete-an-output-window"></a>Eliminar una ventana de salida
 En este ejemplo se muestra cómo eliminar un **salida** panel de ventana.

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

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el **invocar TestOutput** debería ver la ventana de salida con un encabezado que indica que el comando **mostrar resultados desde: Nuevo panel** y las palabras **agregado panel creado** en el propio panel. Si hace clic en el **TestOutput invocar** comando nuevo, se elimina el panel.

## <a name="get-the-general-pane-of-the-output-window"></a>Obtiene el panel General de la ventana de salida
 En este ejemplo se muestra cómo obtener los integrados **General** panel de la **salida** ventana.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Si agrega este método a la extensión dada en la sección anterior, al hacer clic en el **invocar TestOutput** comando debería ver que el **salida** ventana muestra las palabras **encuentra General panel** en el panel.

## <a name="get-the-build-pane-of-the-output-window"></a>Obtiene el panel de compilación de la ventana de salida
 En este ejemplo se muestra cómo buscar el **compilar** panel y escribir en él. Puesto que la **compilar** panel no está activado de forma predeterminada, también se activa.

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
