---
title: Procedimiento Crear una extensión de elemento de proyecto de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 52d2cb187b4c119c17d87e089bdd7e2055556b90
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864776"
---
# <a name="how-to-create-a-sharepoint-project-item-extension"></a>Procedimiento Crear una extensión de elemento de proyecto de SharePoint
  Crear una extensión de elemento de proyecto cuando desea agregar funcionalidad a un elemento de proyecto de SharePoint que ya está instalado en Visual Studio. Para obtener más información, consulte [elementos de proyecto de SharePoint ampliar](../sharepoint/extending-sharepoint-project-items.md).  
  
### <a name="to-create-a-project-item-extension"></a>Para crear una extensión de elemento de proyecto  
  
1.  Cree un proyecto de biblioteca de clases.  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  
  
4.  Agregue los siguientes atributos a la clase:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Este atributo permite que Visual Studio detecte y cargue su <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> tipo al constructor del atributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. En una extensión de elemento de proyecto, este atributo identifica el elemento de proyecto que desea extender. Pasar el identificador del elemento de proyecto al constructor del atributo. Para obtener una lista de los identificadores de los elementos de proyecto que se incluyen con Visual Studio, consulte [elementos de proyecto de SharePoint ampliar](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método, los miembros del uso de la *projectItemType* parámetro para definir el comportamiento de la extensión. Este parámetro es un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objeto que proporciona acceso a los eventos definidos en el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfaces. Para obtener acceso a una instancia específica del tipo de elemento de proyecto está ampliando, controlar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos, como <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo crear una extensión simple para el elemento de proyecto de receptor de eventos. Cada vez que el usuario agrega un elemento de proyecto de receptor de eventos a un proyecto de SharePoint, esta extensión escribe un mensaje en el **salida** ventana y **lista de errores** ventana.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 En este ejemplo usa el servicio de proyecto de SharePoint para escribir el mensaje a la **salida** ventana y **lista de errores** ventana. Para obtener más información, consulte [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compile-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Tutorial: Extender un tipo de elemento de proyecto de SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
