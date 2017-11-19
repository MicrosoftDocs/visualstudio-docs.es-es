---
title: Obtener propiedades del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 931c4c6495d13418ed94f0507a00351e82a92564
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="getting-project-properties"></a>Obtener propiedades del proyecto
Este tutorial se muestra cómo establecer propiedades de proyecto de muestra en una ventana de herramientas.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Para crear un proyecto de VSIX y agregar una ventana de herramientas  
  
1.  Cada extensión de Visual Studio se inicia con un proyecto de implementación de VSIX que contendrá los activos de la extensión. Crear un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `ProjectPropertiesExtension`. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C# / extensibilidad**.  
  
2.  Agregar una ventana de herramientas mediante la adición de una plantilla de elemento de ventana de herramientas personalizada denominada `ProjectPropertiesToolWindow`. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. En el **cuadro de diálogo Agregar nuevo elemento**, vaya a **elementos de Visual C# / extensibilidad** y seleccione **ventana de herramientas personalizada**. En el **nombre** campo en la parte inferior del cuadro de diálogo, cambie el nombre de archivo a `ProjectPropertiesToolWindow.cs`. Para obtener más información sobre cómo crear una ventana de herramientas personalizada, vea [crear una extensión con una ventana de herramientas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Compile la solución y compruebe que se compila sin errores.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Para mostrar las propiedades del proyecto en una ventana de herramientas  
  
1.  En el archivo ProjectPropertiesToolWindowCommand.cs, agregue las siguientes instrucciones using.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  En ProjectPropertiesToolWindowControl.xaml, quite el botón existente y agregar una vista de árbol en el cuadro de herramientas. También puede quitar el controlador de eventos click del archivo ProjectPropertiesToolWindowControl.xaml.cs.  
  
3.  En ProjectPropertiesToolWindowCommand.cs, utilice el método ShowToolWindow() para abrir el proyecto y leer sus propiedades, a continuación, agregue las propiedades para la vista de árbol. El código para ShowToolWindow debe ser similar al siguiente:  
  
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
  
4.  Compile la solución y comience la depuración. Debe aparecer la instancia experimental.  
  
5.  En la instancia experimental, abra un proyecto.  
  
6.  En el **vista / otras ventanas** haga clic en **ProjectPropertiesToolWindow**.  
  
     Debería ver el control de árbol en la ventana de herramienta junto con el nombre del primer proyecto y de todas sus propiedades de proyecto.