---
title: "Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto de SharePoint personalizado | Documentos de Microsoft"
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6875b03c86580328f2e29f701b77c07d646ffca1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Cómo: Agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint
  Cuando se define un tipo de elemento de proyecto de SharePoint personalizado, puede agregar un elemento de menú contextual para el elemento de proyecto. El elemento de menú aparece cuando un usuario seleccione el elemento de proyecto en **el Explorador de soluciones**.  
  
 Los pasos siguientes se supone que ya se ha definido su propio tipo de elemento de proyecto de SharePoint. Para obtener más información, consulte [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Para agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado  
  
1.  En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> eventos de la *projectItemTypeDefinition* parámetro.  
  
2.  En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, agregue un nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> el objeto a la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> colección del parámetro de argumentos del evento.  
  
3.  En el <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> controlador de eventos para el nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> objeto, lleve a cabo las tareas que desea ejecutar cuando un usuario elige el elemento de menú contextual.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado. Cuando el usuario abra el menú contextual del elemento de proyecto de **el Explorador de soluciones** y elige el **escribir mensaje de la ventana de salida** elemento de menú, Visual Studio muestra un mensaje en el **salida**  ventana.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 Este ejemplo utiliza el servicio de proyecto de SharePoint para escribir el mensaje a la **salida** ventana. Para obtener más información, consulte [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Compilar el código  
 En este ejemplo se necesita un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Implementar el elemento de proyecto  
 Para permitir que otros desarrolladores usen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto. Para obtener más información, consulte [crear plantillas de elementos y las plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implementar el elemento de proyecto, crear un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado, la plantilla y cualquier otro archivo que desee distribuir con el elemento de proyecto. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Cómo: agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Definición de tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  