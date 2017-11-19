---
title: "Cómo: crear un elemento Web de SharePoint | Documentos de Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 847124dc9a7e4cd80993df5b50c5d3d3b752f228
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Cómo: Crear un elemento web de SharePoint
  Puede crear y personalizar un elemento web agregando un **elemento Web** elemento a un proyecto de SharePoint y, a continuación, modificar el archivo de código para el elemento web o utilizando un diseñador. Para obtener más información, consulte [Cómo: crear un elemento Web de SharePoint utilizando un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Para crear un elemento web de SharePoint  
  
1.  Cree o abra un proyecto de SharePoint.  
  
     Para obtener más información, consulte [proyecto de SharePoint y plantillas de elementos de proyecto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Elija el nodo de proyecto de SharePoint en **el Explorador de soluciones** y, a continuación, elija **proyecto**, **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
4.  En la lista de plantillas de SharePoint, elija **elemento Web**.  
  
5.  En el **nombre** cuadro, especifique un nombre para el elemento web y, a continuación, elija la **agregar** botón.  
  
     El elemento web aparece en **el Explorador de soluciones**. Para obtener más información acerca de los archivos que incluye un elemento web, consulte [crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  En **el Explorador de soluciones**, abra el archivo de código para el elemento web que acaba de crear.  
  
     Por ejemplo, si el nombre del elemento web es WebPart1, abra WebPart1.vb (en Visual Basic) o WebPart1.cs (en C#).  
  
7.  En el archivo de código, agregue controles al método <xref:System.Web.UI.Control.CreateChildControls%2A>.  
  
     Para obtener un ejemplo, vea [Tutorial: crear un elemento Web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Cómo: crear un elemento Web de SharePoint utilizando un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Tutorial: Crear un elemento Web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Tutorial: Crear un elemento web para SharePoint mediante un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  