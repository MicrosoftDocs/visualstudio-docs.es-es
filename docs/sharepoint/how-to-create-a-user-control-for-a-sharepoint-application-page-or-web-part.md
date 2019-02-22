---
title: Filtrar Crear un Control de usuario para una página de aplicación de SharePoint o elemento Web | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 29557d14644971ade86048aebee670ba35cff784
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633075"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Procedimiento Crear un control de usuario para un elemento de página o web de la aplicación de SharePoint
  Puede crear controles de usuario personalizados que proporcionan funcionalidad personalizada para la solución de SharePoint, y puede reutilizar esa funcionalidad dentro del proyecto. Puede incluir controles de usuario en un elemento web o página de aplicación, agregar más controles ASP.NET y controles de SharePoint, así como definir propiedades y métodos para el control. Para obtener más información acerca de los controles de usuario, consulte [crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) y [controles de usuario y controles de servidor de SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Para crear un control de usuario para SharePoint

1.  En Visual Studio, abra o cree un proyecto de SharePoint.

     Consulte [SharePoint plantillas de elemento de proyecto y](../sharepoint/sharepoint-project-and-project-item-templates.md).

2.  En el **Explorador de soluciones**, elija el nodo de proyecto.

3.  En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

4.  En el **instalado** panel, elija el **Office/SharePoint** nodo.

5.  En la lista de plantillas de SharePoint, elija **Control de usuario (solución de granja de servidores únicamente)**.

    > [!NOTE]
    >  Los controles de usuario funcionan solo en soluciones de granja.

6.  En el **nombre** cuadro, especifique un nombre para el control de usuario y, a continuación, elija el **agregar** botón.

     Visual Studio agrega varias carpetas y archivos al proyecto. Para obtener más información acerca de estos archivos, consulte [crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     De forma predeterminada, el archivo de control de usuario aparece en el **origen** la vista del Diseñador de Visual Web Developer. En esta vista, puede modificar el marcador XML del control. Puede cambiar a **diseño** ver si desea diseñar el control visualmente arrastrando controles desde el **cuadro de herramientas**. Consulte [vista Diseño, el Diseñador de páginas Web](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7.  Si desea controlar los eventos que se producen en el control, agregue código al archivo de código del control de usuario.

     Este archivo aparece en **el Explorador de soluciones** en el archivo de control de usuario y tiene un *.cs* o *.vb* extensión, dependiendo del lenguaje del proyecto.

## <a name="see-also"></a>Vea también
- [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
