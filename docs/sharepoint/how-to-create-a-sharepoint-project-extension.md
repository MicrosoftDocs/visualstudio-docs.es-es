---
title: "Cómo: crear una extensión de proyecto de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 04/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fb0c28ee6f9408ed417f570ce4a3ab1dc500c295
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>Cómo: Crear una extensión de proyecto de SharePoint
  Crear una extensión de proyecto cuando desee agregar funcionalidad a un proyecto de SharePoint que esté abierto en Visual Studio. Para obtener más información, consulte [extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  

### <a name="to-create-a-project-extension"></a>Para crear una extensión de proyecto  

1.  Cree un proyecto de biblioteca de clases.  

2.  Agregue referencias a los siguientes ensamblados:  

    -   Microsoft.VisualStudio.SharePoint  

    -   System.ComponentModel.Composition  

3.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  

4.  Agregue el <xref:System.ComponentModel.Composition.ExportAttribute> a la clase. Este atributo permite que Visual Studio detecte y cargue el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación. Pasar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo al constructor de atributo.  

5.  En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método, los miembros del uso de la *projectService* parámetro para definir el comportamiento de la extensión. Este parámetro es un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto que proporciona acceso a los eventos definidos en el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> interfaz.  

## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo crear una extensión de proyecto simple que controla la mayoría de los eventos de proyecto de SharePoint que se definen mediante la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> interfaz. Para probar el código, cree un proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y, a continuación, agregar más proyectos a la solución, cambiar los valores de propiedad de proyecto, o elimine o excluya un proyecto. La extensión le informa de los eventos mediante la escritura de mensajes a la **salida** ventana y **lista de errores** ventana.  

  ```vb  
    Imports Microsoft.VisualStudio.SharePoint
    Imports System.ComponentModel
    Imports System.ComponentModel.Composition

    Namespace Contoso.ExampleProjectExtension
      <Export(GetType(ISharePointProjectExtension))> _
      Class ExampleProjectExtension
        Implements ISharePointProjectExtension

        Private WithEvents projectService As ISharePointProjectService

        Public Sub Initialize(ByVal projectService As ISharePointProjectService) _
            Implements ISharePointProjectExtension.Initialize
            Me.projectService = projectService
        End Sub

        ' A project was added.
        Private Sub projectService_ProjectAdded(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectAdded
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was added: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was loaded in the IDE.
        Private Sub projectService_ProjectInitialized(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectInitialized
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being initialized: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' The name of a property was changed.
        Private Sub projectService_ProjectNameChanged(ByVal sender As Object, ByVal e As NameChangedEventArgs) _
            Handles projectService.ProjectNameChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project property value was changed.
        Private Sub ProjectPropertyChanged(ByVal sender As Object, ByVal e As PropertyChangedEventArgs) _
            Handles projectService.ProjectPropertyChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project is being removed or unloaded.
        Private Sub projectService_ProjectRemoved(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectRemoved
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was removed or unloaded.
        Private Sub projectService_ProjectDisposing(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectDisposing
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub
      End Class
    End Namespace  
    ```  

    ```csharp  
    using Microsoft.VisualStudio.SharePoint;
    using System;
    using System.ComponentModel;
    using System.ComponentModel.Composition;

    namespace Contoso.ExampleProjectExtension
    {
      [Export(typeof(ISharePointProjectExtension))]
      internal class ExampleProjectExtension : ISharePointProjectExtension
      {
        public void Initialize(ISharePointProjectService projectService)
        {
            projectService.ProjectAdded += projectService_ProjectAdded;
            projectService.ProjectInitialized += projectService_ProjectInitialized;
            projectService.ProjectNameChanged += projectService_ProjectNameChanged;
            projectService.ProjectPropertyChanged += projectService_ProjectPropertyChanged;
            projectService.ProjectRemoved += projectService_ProjectRemoved;
            projectService.ProjectDisposing += projectService_ProjectDisposing;
        }

        // A project was added.
        void projectService_ProjectAdded(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was added: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is loaded in the IDE.
        void projectService_ProjectInitialized(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being initialized: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // The name of a project was changed.
        void projectService_ProjectNameChanged(object sender, NameChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project property value was changed.
        private void projectService_ProjectPropertyChanged(object sender, PropertyChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is being removed or unloaded.
        void projectService_ProjectRemoved(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project was removed or unloaded.
        void projectService_ProjectDisposing(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }
     }
  }  
  ```  

Este ejemplo utiliza el servicio de proyecto de SharePoint para escribir el mensaje a la **salida** ventana y **lista de errores** ventana. Para obtener más información, consulte [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  

 Para obtener ejemplos que muestran cómo controlar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> los eventos, vea [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) y [Cómo: agregar una propiedad a los proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  

## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los siguientes ensamblados:  

-   Microsoft.VisualStudio.SharePoint  

-   System.ComponentModel.Composition  

## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  

## <a name="see-also"></a>Vea también  
 [Extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Cómo: agregar una propiedad a los proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Tutorial: Creación de una extensión de proyecto de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
