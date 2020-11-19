---
title: 'Cómo: crear un elemento Web de SharePoint | Microsoft Docs'
description: Crear y personalizar un elemento Web mediante un diseñador, o agregando un elemento de elemento Web a cualquier proyecto de SharePoint y editando después el archivo de código para el elemento Web.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 13039520299d52e6f6a704567cf1cdc5ccfd66db
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903707"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Cómo: para crear un elemento web de SharePoint
  Puede crear y personalizar un elemento Web agregando un elemento de **elemento Web** a cualquier proyecto de SharePoint y, a continuación, editando el archivo de código para el elemento Web o mediante un diseñador. Para obtener más información, vea [Cómo: crear un elemento Web de SharePoint mediante un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>Para crear un elemento Web de SharePoint

1. Cree o abra un proyecto de SharePoint.

     Para obtener más información, vea [plantillas de proyecto y de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Elija el nodo del proyecto de SharePoint en **Explorador de soluciones** y, a continuación, elija **proyecto**  >  **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010** .

4. En la lista de plantillas de SharePoint, elija **elemento Web**.

5. En el cuadro **nombre** , especifique un nombre para el elemento Web y, a continuación, elija el botón **Agregar** .

     El elemento Web aparece en **Explorador de soluciones**. Para obtener más información acerca de los archivos que incluye un elemento Web, vea [crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

6. En **Explorador de soluciones**, abra el archivo de código para el elemento Web que acaba de crear.

     Por ejemplo, si el nombre del elemento Web es *WebPart1*, Abra *WebPart1. vb* (en Visual Basic) o *WebPart1.CS* (en C#).

7. En el archivo de código, agregue controles al método <xref:System.Web.UI.Control.CreateChildControls%2A>.

     Para obtener un ejemplo, vea [Tutorial: crear un elemento Web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Consulte también
- [Creación de elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Cómo: para crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Tutorial: Creación de un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Tutorial: Creación de un elemento web para SharePoint mediante un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
