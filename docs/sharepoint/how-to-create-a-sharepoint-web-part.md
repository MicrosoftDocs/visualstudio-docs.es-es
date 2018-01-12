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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 27826859d2bac9b247132e7fcb2c3721b6d38092
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
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
  
  