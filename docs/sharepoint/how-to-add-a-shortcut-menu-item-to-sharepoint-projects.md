---
title: 'Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4e43d8d7717302eb8ab250935188bc2db3bdd66a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014838"
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Cómo: agregar un elemento de menú contextual a los proyectos de SharePoint
  Puede Agregar un elemento de menú contextual a cualquier proyecto de SharePoint. El elemento de menú aparece cuando un usuario hace clic con el botón secundario en un nodo de proyecto en **Explorador de soluciones**.

 En los pasos siguientes se supone que ya ha creado una extensión de proyecto. Para obtener más información, vea [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Para agregar un elemento de menú contextual a los proyectos de SharePoint

1. En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento del parámetro *projectService* .

2. En el controlador de eventos del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento, agregue un nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objeto a la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> colección o del parámetro de argumentos de evento.

3. En el <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> controlador de eventos para el nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objeto, realice las tareas que desea ejecutar cuando un usuario hace clic en el elemento de menú contextual.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo agregar un elemento de menú contextual a los nodos de proyecto de SharePoint en **Explorador de soluciones**. Cuando el usuario hace clic con el botón secundario en un nodo de proyecto y hace clic en el elemento de menú **escribir mensaje para ventana de salida** , Visual Studio muestra un mensaje en la ventana de **salida** . En este ejemplo se usa el servicio de proyecto de SharePoint para mostrar el mensaje. Para obtener más información, vea [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Cómo: agregar una propiedad a proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
