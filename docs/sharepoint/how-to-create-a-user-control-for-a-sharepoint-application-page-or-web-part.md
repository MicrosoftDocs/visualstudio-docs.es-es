---
title: 'Cómo: crear un Control de usuario para una página de aplicación de SharePoint o elemento Web | Microsoft Docs'
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
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 98333049f711e9d28d7adb1ad0c17cfc8514e4ad
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119387"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Cómo: crear un control de usuario para un elemento de página o web de la aplicación de SharePoint
  Puede crear controles de usuario personalizados que proporcionan funcionalidad personalizada para la solución de SharePoint, y puede reutilizar esa funcionalidad dentro del proyecto. Puede incluir controles de usuario en un elemento web o página de aplicación, agregar más controles ASP.NET y controles de SharePoint, así como definir propiedades y métodos para el control. Para obtener más información acerca de los controles de usuario, consulte [crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) y [controles de usuario y controles de servidor de SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
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
  
     De forma predeterminada, el archivo de control de usuario aparece en el **origen** la vista del Diseñador de Visual Web Developer. En esta vista, puede modificar el marcador XML del control. Puede cambiar a **diseño** ver si desea diseñar el control visualmente arrastrando controles desde el **cuadro de herramientas**. Consulte [vista Diseño, el Diseñador de páginas Web](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Si desea controlar los eventos que se producen en el control, agregue código al archivo de código del control de usuario.  
  
     Este archivo aparece en **el Explorador de soluciones** en el archivo de control de usuario y tiene un *.cs* o *.vb* extensión, dependiendo del lenguaje del proyecto.  
  
## <a name="see-also"></a>Vea también
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
