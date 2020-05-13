---
title: Obtención de las propiedades del proyecto ? Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711408"
---
# <a name="get-project-properties"></a>Obtener propiedades del proyecto

En este tutorial se muestra cómo mostrar las propiedades del proyecto en una ventana de herramientas.

## <a name="prerequisites"></a>Prerrequisitos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Para crear un proyecto VSIX y agregar una ventana de herramientas

1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX, que contendrá los activos de extensión. Cree [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un proyecto `ProjectPropertiesExtension`VSIX denominado . Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".

2. Agregue una ventana de herramientas agregando `ProjectPropertiesToolWindow`una plantilla de elemento de ventana de herramientas personalizada denominada . En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. En el cuadro de **diálogo Agregar nuevo elemento**, vaya a**Extensibilidad** de elementos > de **Visual C.** y seleccione Ventana de **herramientas personalizadas**. En el campo **Nombre** en la parte inferior `ProjectPropertiesToolWindow.cs`del cuadro de diálogo, cambie el nombre del archivo a . Para obtener más información sobre cómo crear una ventana de herramientas personalizada, consulte [Crear una extensión con una ventana](../extensibility/creating-an-extension-with-a-tool-window.md)de herramientas .

3. Compile la solución y compruebe que se compila sin errores.

### <a name="to-display-project-properties-in-a-tool-window"></a>Para mostrar las propiedades del proyecto en una ventana de herramientas

1. En el archivo ProjectPropertiesToolWindowCommand.cs, agregue las siguientes directivas using.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. En *ProjectPropertiesToolWindowControl.xaml*, quite el botón existente y agregue un TreeView desde el cuadro de herramientas. También puede quitar el controlador de eventos click del archivo *ProjectPropertiesToolWindowControl.xaml.cs.*

3. En *ProjectPropertiesToolWindowCommand.cs*, `ShowToolWindow()` utilice el método para abrir el proyecto y leer sus propiedades y, a continuación, agregue las propiedades a TreeView. El código de ShowToolWindow debe tener el siguiente aspecto:

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. Compile la solución y comience la depuración. Debería aparecer la instancia experimental.

5. En la instancia experimental, abra un proyecto.

6. En **Ver** > **otras ventanas,** haga clic en **ProjectPropertiesToolWindow**.

  Debería ver el control de árbol en la ventana de herramientas junto con el nombre del primer proyecto y de todas sus propiedades del proyecto.
