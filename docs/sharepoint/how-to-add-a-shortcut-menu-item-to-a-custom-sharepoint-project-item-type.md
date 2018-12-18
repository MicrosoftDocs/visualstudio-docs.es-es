---
title: 'Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 580839936cfa42b4e76999809cd8917f3eb4f041
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755507"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Cómo: agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado de SharePoint
  Al definir un tipo de elemento de proyecto de SharePoint personalizado, puede agregar un elemento de menú contextual para el elemento de proyecto. El elemento de menú aparece cuando un usuario del botón secundario en el elemento de proyecto **el Explorador de soluciones**.  
  
 Los pasos siguientes se supone que ya se ha definido su propio tipo de elemento de proyecto de SharePoint. Para obtener más información, consulte [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Para agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado  
  
1.  En el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método de su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementación, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> eventos de la *projectItemTypeDefinition* parámetro.  
  
2.  En el controlador de eventos para el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, agregue un nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de objeto para el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> colección del parámetro de argumentos del evento.  
  
3.  En el <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> controlador de eventos para el nuevo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de objetos, realizar las tareas que desee ejecutar cuando un usuario elige el elemento de menú contextual.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente muestra cómo agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado. Cuando el usuario abre el menú contextual del elemento de proyecto en **el Explorador de soluciones** y elige el **escribir mensaje de la ventana de salida** elemento de menú, Visual Studio muestra un mensaje en el **salida**  ventana.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 En este ejemplo usa el servicio de proyecto de SharePoint para escribir el mensaje a la **salida** ventana. Para obtener más información, consulte [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Compile el código  
 Este ejemplo requiere un proyecto de biblioteca de clases con referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-project-item"></a>Implementar el elemento de proyecto  
 Para permitir que otros desarrolladores usen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto. Para obtener más información, consulte [crear elementos de plantillas y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implementar el elemento de proyecto, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado, la plantilla y cualquier otro archivo que desea distribuir con el elemento de proyecto. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Cómo: agregar una propiedad a un tipo de elemento de proyecto personalizado de SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Definir tipos de elemento de proyecto de SharePoint personalizados](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
 
