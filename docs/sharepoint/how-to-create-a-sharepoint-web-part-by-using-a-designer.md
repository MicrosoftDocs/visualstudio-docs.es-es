---
title: 'Cómo: crear un elemento Web de SharePoint mediante un diseñador | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 0830cec748d68f010397c42334a5ed83365ee6b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016479"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Cómo: crear un elemento Web de SharePoint mediante un diseñador
  Puede crear un elemento Web agregando un elemento de **elemento Web visual** a cualquier proyecto de SharePoint. Se abre el diseñador de Visual Web Developer en Visual Studio donde puede agregar controles y código al elemento web. Los elementos web visuales funcionan de la misma manera que lo hacen los elementos web. La única diferencia es que el usuario diseña los elementos web visuales en el diseñador de Visual Web Developer.

### <a name="to-create-a-project-for-visual-web-parts"></a>Para crear un proyecto de elementos web visuales

1. En la barra de menús, elija **Archivo** >**Nuevo** > **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

2. En el cuadro de diálogo **nuevo proyecto** , en **Visual C#** o **Visual Basic**, expanda el nodo **Office/SharePoint** y, a continuación, elija la categoría **soluciones de SharePoint** .

3. En la lista de plantillas de proyecto, elija **SharePoint 2013-elemento Web visual**y, a continuación, elija el botón **Aceptar** .

     Aparece el **Asistente para la personalización de SharePoint** .

4. En la página **especifique el sitio y el nivel de seguridad de la depuración** , especifique la dirección URL de un sitio de SharePoint que se encuentra en el equipo local y, a continuación, elija el botón **Finalizar** .

     En **Explorador de soluciones**, aparece un elemento Web. Después de diseñar el elemento Web en el diseñador de Visual Web Developer, lo probará en el sitio que especifique.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Para agregar un elemento web visual a un proyecto de SharePoint existente

1. En la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , elija el nodo **Office/SharePoint** .

3. En la lista de plantillas de proyecto, elija **elemento Web visual**, asígnele el nombre y, a continuación, elija el botón **Agregar** .

     En **Explorador de soluciones**, aparece el elemento Web. Después de diseñar el elemento Web en el diseñador de Visual Web Developer, lo probará en el sitio que especifique.

## <a name="see-also"></a>Consulte también
- [Crear elementos Web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Cómo: crear un elemento Web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Tutorial: crear un elemento Web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Tutorial: crear un elemento Web para SharePoint mediante un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
