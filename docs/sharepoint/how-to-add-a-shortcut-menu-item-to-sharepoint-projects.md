---
title: "Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
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
ms.openlocfilehash: c8cf3a3705fd389f16ac02d5739eeb754df99ac9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Cómo: Agregar un elemento de menú contextual a los proyectos de SharePoint
  Puede agregar un elemento de menú contextual a un proyecto de SharePoint. El elemento de menú aparece cuando un usuario seleccione un nodo de proyecto en **el Explorador de soluciones**.  
  
 Los pasos siguientes se supone que ya ha creado una extensión de proyecto. Para obtener más información, consulte [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Para agregar un elemento de menú contextual a los proyectos de SharePoint  
  
1.  En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> eventos de la *projectService* parámetro.  
  
2.  En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento, agregue un nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> el objeto a la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> colección del parámetro de argumentos del evento.  
  
3.  En el <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> controlador de eventos para el nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objeto, lleve a cabo las tareas que desea ejecutar cuando un usuario hace clic en el elemento de menú contextual.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar un elemento de menú contextual a los nodos de proyecto de SharePoint en **el Explorador de soluciones**. Cuando el usuario hace clic con el botón un nodo de proyecto y haga clic en el **escribir mensaje de la ventana de salida** elemento de menú, Visual Studio muestra un mensaje en el **salida** ventana. En este ejemplo se usa el servicio de proyecto de SharePoint para mostrar el mensaje. Para obtener más información, consulte [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 En este ejemplo se necesita un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Cómo: Agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  