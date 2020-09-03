---
title: Agregar elemento de menú contextual a la extensión de elemento de proyecto de SharePoint
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5c0515fddc106418902cd2cca9fcba4c0e365da1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014852"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension"></a>Cómo: agregar un elemento de menú contextual a una extensión de elemento de proyecto de SharePoint
  Puede Agregar un elemento de menú contextual a un elemento de proyecto de SharePoint existente mediante una extensión de elemento de proyecto. El elemento de menú aparece cuando un usuario hace clic con el botón secundario en el elemento de proyecto en **Explorador de soluciones**.

 En los pasos siguientes se supone que ya ha creado una extensión de elemento de proyecto. Para obtener más información, vea [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-shortcut-menu-item-in-a-project-item-extension"></a>Para agregar un elemento de menú contextual en una extensión de elemento de proyecto

1. En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementación, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento del parámetro *projectItemType* .

2. En el controlador de eventos del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, agregue un nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objeto a la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> colección o del parámetro de argumentos de evento.

3. En el <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> controlador de eventos para el nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objeto, realice las tareas que desea ejecutar cuando un usuario hace clic en el elemento de menú contextual.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo agregar un elemento de menú contextual al elemento de proyecto del receptor de eventos. Cuando el usuario hace clic con el botón secundario en el elemento de proyecto de **Explorador de soluciones** y hace clic en el elemento de menú **escribir mensaje para ventana de salida** , Visual Studio muestra un mensaje en la ventana de **salida** .

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionmenu.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionmenu.cs#1)]

 En este ejemplo se usa el servicio de proyecto de SharePoint para escribir el mensaje en la ventana de **salida** . Para obtener más información, vea [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Cómo: agregar una propiedad a una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Tutorial: extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
