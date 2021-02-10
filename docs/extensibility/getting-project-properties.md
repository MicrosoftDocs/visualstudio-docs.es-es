---
title: Obtener propiedades del proyecto | Microsoft Docs
description: Obtenga información sobre cómo mostrar las propiedades del proyecto en una ventana de herramientas. En este ejemplo se muestra el control de árbol en la ventana de herramientas.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e89a19ee51a62e8d92c0ec8984e912703e2b92b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968195"
---
# <a name="get-project-properties"></a>Obtener propiedades del proyecto

En este tutorial se muestra cómo mostrar las propiedades del proyecto en una ventana de herramientas.

## <a name="prerequisites"></a>Requisitos previos

A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Para crear un proyecto VSIX y agregar una ventana de herramientas

1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX, que contendrá los recursos de la extensión. Cree un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Proyecto VSIX denominado `ProjectPropertiesExtension` . Para buscar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , busque "VSIX".

2. Agregue una ventana de herramientas agregando una plantilla de elemento de ventana de herramientas personalizada denominada `ProjectPropertiesToolWindow` . En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. En el **cuadro de diálogo Agregar nuevo elemento**, vaya a la extensibilidad de **elementos de Visual C#**  >   y seleccione **ventana de herramientas personalizada**. En el campo **nombre** de la parte inferior del cuadro de diálogo, cambie el nombre del archivo a `ProjectPropertiesToolWindow.cs` . Para obtener más información sobre cómo crear una ventana de herramientas personalizada, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Compile la solución y compruebe que se compila sin errores.

### <a name="to-display-project-properties-in-a-tool-window"></a>Para mostrar las propiedades del proyecto en una ventana de herramientas

1. En el archivo ProjectPropertiesToolWindowCommand.cs, agregue las siguientes directivas using.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. En *ProjectPropertiesToolWindowControl. Xaml*, quite el botón existente y agregue una vista de árbol desde el cuadro de herramientas. También puede quitar el controlador de eventos Click del archivo *ProjectPropertiesToolWindowControl.Xaml.CS* .

3. En *ProjectPropertiesToolWindowCommand.CS*, use el `ShowToolWindow()` método para abrir el proyecto y leer sus propiedades y, a continuación, agregue las propiedades a la vista de árbol. El código de ShowToolWindow debe tener un aspecto similar al siguiente:

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

6. En la **vista**  >  **otras ventanas** , haga clic en **ProjectPropertiesToolWindow**.

  Debería ver el control de árbol en la ventana de herramientas junto con el nombre del primer proyecto y de todas sus propiedades del proyecto.
