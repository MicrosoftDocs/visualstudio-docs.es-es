---
title: Filtrar Crear un elemento Web de SharePoint utilizando un diseñador | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c049a6f6a5d57ea5c283b262f6f975c0838ac94f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596373"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Filtrar Crear un elemento Web de SharePoint mediante un diseñador
  Puede crear un elemento web agregando un **elemento Web Visual** a un proyecto de SharePoint. Se abre el diseñador de Visual Web Developer en Visual Studio donde puede agregar controles y código al elemento web. Los elementos web visuales funcionan de la misma manera que lo hacen los elementos web. La única diferencia es que el usuario diseña los elementos web visuales en el diseñador de Visual Web Developer.

### <a name="to-create-a-project-for-visual-web-parts"></a>Para crear un proyecto de elementos web visuales

1.  En la barra de menús, elija **Archivo** >**Nuevo** > **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

2.  En el **nuevo proyecto** cuadro de diálogo, bajo **Visual C#** o **Visual Basic**, expanda el **Office/SharePoint** nodo y, a continuación, elija el **soluciones de SharePoint** categoría.

3.  En la lista de plantillas de proyecto, elija **SharePoint 2013 - elemento Web Visual**y, a continuación, elija el **Aceptar** botón.

     El **Asistente de personalización de SharePoint** aparece.

4.  En el **especificar el nivel de sitio y de seguridad para la depuración** página, especifique la dirección URL de un sitio de SharePoint que se encuentra en el equipo local, y, a continuación, elija el **finalizar** botón.

     En **el Explorador de soluciones**, aparece un elemento web. Después de diseñar el elemento web en el Diseñador de Visual Web Developer, probará en el sitio que especifique.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Para agregar un elemento web visual a un proyecto de SharePoint existente

1.  En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

2.  En el **Agregar nuevo elemento** diálogo cuadro, elija el **Office/SharePoint** nodo.

3.  En la lista de plantillas de proyecto, elija **elemento Web Visual**, asígnele el nombre y, a continuación, elija el **agregar** botón.

     En **el Explorador de soluciones**, aparece el elemento web. Después de diseñar el elemento web en el Diseñador de Visual Web Developer, probará en el sitio que especifique.

## <a name="see-also"></a>Vea también
- [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Cómo: Crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Tutorial: Crear un elemento web para SharePoint utilizando un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
