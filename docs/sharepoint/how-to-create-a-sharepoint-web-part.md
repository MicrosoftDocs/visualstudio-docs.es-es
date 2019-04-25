---
title: Procedimiento Crear un elemento Web de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 304e9f29d317a5258467e4ff45248d0dd2066d4f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041126"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Procedimiento Crear un elemento web de SharePoint
  Puede crear y personalizar un elemento web agregando un **elemento Web** elemento a cualquier proyecto de SharePoint y, a continuación, modificar el archivo de código para el elemento web o utilizando un diseñador. Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>Para crear un elemento web de SharePoint

1. Cree o abra un proyecto de SharePoint.

     Para obtener más información, consulte [SharePoint plantillas de elemento de proyecto y](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Elija el nodo de proyecto de SharePoint en **el Explorador de soluciones** y, a continuación, elija **proyecto** > **Agregar nuevo elemento**.

3. En el **Agregar nuevo elemento** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija el **2010** nodo.

4. En la lista de plantillas de SharePoint, elija **elemento Web**.

5. En el **nombre** cuadro, especifique un nombre para el elemento web y, a continuación, elija el **agregar** botón.

     El elemento web aparece en **el Explorador de soluciones**. Para obtener más información acerca de los archivos que incluye un elemento web, consulte [crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

6. En **el Explorador de soluciones**, abra el archivo de código para el elemento web que acaba de crear.

     Por ejemplo, si es el nombre del elemento web *WebPart1*, abra *WebPart1.vb* (en Visual Basic) o *WebPart1.cs* (en C#).

7. En el archivo de código, agregue controles al método <xref:System.Web.UI.Control.CreateChildControls%2A>.

     Para obtener un ejemplo, vea [Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Vea también
- [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Cómo: Crear un elemento web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Tutorial: Crear un elemento web para SharePoint utilizando un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
