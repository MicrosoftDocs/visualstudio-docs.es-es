---
title: Filtrar Crear una página de aplicación | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16c772ac411669cde082475840197ec2f12c9fb2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646543"
---
# <a name="how-to-create-an-application-page"></a>Filtrar Crear una página de aplicación
  Puede crear una página web ASP.NET para uno o varios sitios de SharePoint. En SharePoint, estas páginas se denominan páginas de aplicación. A diferencia de una página del sitio, una página de aplicación contiene código que se ejecuta detrás de la página. Para obtener más información, consulte [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Para crear una página de aplicación

1.  En Visual Studio, abra o cree un proyecto de SharePoint.

     Para obtener más información, consulte [SharePoint plantillas de elemento de proyecto y](../sharepoint/sharepoint-project-and-project-item-templates.md).

2.  En el **Explorador de soluciones**, elija el nodo de proyecto.

3.  En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

4.  En el **Agregar nuevo elemento** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija el **2010** elemento.

5.  En la lista de plantillas de SharePoint, elija **página aplicación**.

6.  En el **nombre** cuadro, especifique un nombre para la página de aplicación y, a continuación, elija el **agregar** botón.

     Visual Studio agrega varias carpetas y archivos al proyecto. Para obtener más información acerca de estos archivos, consulte [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     En el **origen** muestra la vista del Diseñador de Visual Web Developer, el archivo de paginación ASP.NET. Puede diseñar la página agregando controles desde el **cuadro de herramientas** y colocarlas en marcadores de posición de contenido. Para obtener más información, consulte [vista código fuente, Diseñador de páginas Web](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7.  Si desea controlar los eventos de control, agregue código al archivo de código para la página de aplicación.

     El archivo de código aparece si expande el nodo para el archivo de página ASP.NET y tiene un *.cs* o *.vb* extensión, dependiendo del lenguaje del proyecto. Para obtener un ejemplo de extremo a extremo de creación de una página de aplicación, consulte [Tutorial: Crear una página de aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Vea también
- [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Tutorial: Crear una página de aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
