---
title: Crear control de usuario para la página de aplicación de SharePoint o el elemento Web
titleSuffix: ''
description: Cree controles de usuario personalizados que proporcionen funcionalidad personalizada para su solución de SharePoint y vuelva a usar esa funcionalidad en un elemento Web o una página de aplicación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: cbaeaff14d365f41bff73c29e678a08130b03dc0
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903681"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Cómo: para crear un control de usuario para una página de aplicación o elemento web de SharePoint
  Puede crear controles de usuario personalizados que proporcionan funcionalidad personalizada para la solución de SharePoint, y puede reutilizar esa funcionalidad dentro del proyecto. Puede incluir controles de usuario en un elemento web o página de aplicación, agregar más controles ASP.NET y controles de SharePoint, así como definir propiedades y métodos para el control. Para obtener más información sobre los controles de usuario, vea [crear controles reutilizables para elementos Web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) , y controles [de usuario y controles de servidor en SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Para crear un control de usuario para SharePoint

1. En Visual Studio, abra o cree un proyecto de SharePoint.

     Vea [plantillas de proyecto y de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. En el **Explorador de soluciones**, elija el nodo de proyecto.

3. En la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.

4. En el panel **instalado** , elija el nodo **Office/SharePoint** .

5. En la lista de plantillas de SharePoint, elija **control de usuario (solo solución de granja de servidores)**.

    > [!NOTE]
    > Los controles de usuario funcionan solo en soluciones de granja.

6. En el cuadro **nombre** , especifique un nombre para el control de usuario y, a continuación, elija el botón **Agregar** .

     Visual Studio agrega varias carpetas y archivos al proyecto. Para obtener más información acerca de estos archivos, vea [crear controles reutilizables para elementos Web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     De forma predeterminada, el archivo de control de usuario aparece en la vista **código fuente** del diseñador de Visual Web Developer. En esta vista, puede modificar el marcador XML del control. Puede cambiar a la vista de **diseño** si desea diseñar el control visualmente arrastrando los controles del cuadro de **herramientas**. Vea [vista de diseño, diseñador de páginas web](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Si desea controlar los eventos que se producen en el control, agregue código al archivo de código del control de usuario.

     Este archivo aparece en **Explorador de soluciones** bajo el archivo de control de usuario y tiene una extensión *. CS* o *. VB* , dependiendo del lenguaje del proyecto.

## <a name="see-also"></a>Consulte también
- [Creación de controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Creación de páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Creación de elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
