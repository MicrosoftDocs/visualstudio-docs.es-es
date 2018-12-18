---
title: 'Cómo: crear un elemento Web de SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6437620b4215726ba48ea3234e37c76e77d21ebe
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119840"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Cómo: crear un elemento web de SharePoint
  Puede crear y personalizar un elemento web agregando un **elemento Web** elemento a cualquier proyecto de SharePoint y, a continuación, modificar el archivo de código para el elemento web o utilizando un diseñador. Para obtener más información, consulte [Cómo: crear un elemento web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Para crear un elemento web de SharePoint
  
1.  Cree o abra un proyecto de SharePoint.  
  
     Para obtener más información, consulte [SharePoint plantillas de elemento de proyecto y](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Elija el nodo de proyecto de SharePoint en **el Explorador de soluciones** y, a continuación, elija **proyecto** > **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.  
  
4.  En la lista de plantillas de SharePoint, elija **elemento Web**.  
  
5.  En el **nombre** cuadro, especifique un nombre para el elemento web y, a continuación, elija el **agregar** botón.  
  
     El elemento web aparece en **el Explorador de soluciones**. Para obtener más información acerca de los archivos que incluye un elemento web, consulte [crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  En **el Explorador de soluciones**, abra el archivo de código para el elemento web que acaba de crear.  
  
     Por ejemplo, si es el nombre del elemento web *WebPart1*, abra *WebPart1.vb* (en Visual Basic) o *WebPart1.cs* (en C#).  
  
7.  En el archivo de código, agregue controles al método <xref:System.Web.UI.Control.CreateChildControls%2A>.  
  
     Para obtener un ejemplo, vea [Tutorial: crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Vea también
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Cómo: crear un elemento web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Tutorial: Crear un elemento web para SharePoint utilizando un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  
