---
title: 'Cómo: crear una página de aplicación | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 32e6fbb7cece4c3b7513dfc1f5de3aca22f145ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016948"
---
# <a name="how-to-create-an-application-page"></a>Cómo: crear una página de aplicación
  Puede crear una página web de ASP.NET para uno o varios sitios de SharePoint. En SharePoint, estas páginas se denominan páginas de aplicación. A diferencia de una página de sitio, una página de aplicación contiene código que se ejecuta detrás de la página. Para obtener más información, vea [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Para crear una página de aplicación

1. En Visual Studio, abra o cree un proyecto de SharePoint.

     Para obtener más información, vea [plantillas de proyecto y de elemento de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. En el **Explorador de soluciones**, elija el nodo de proyecto.

3. En la barra de menús, elija **proyecto**  >  **Agregar nuevo elemento**.

4. En el cuadro de diálogo **Agregar nuevo elemento** , expanda el nodo **SharePoint** y, a continuación, elija el elemento **2010** .

5. En la lista de plantillas de SharePoint, elija **Página de aplicación**.

6. En el cuadro **nombre** , especifique un nombre para la página de la aplicación y, a continuación, elija el botón **Agregar** .

     Visual Studio agrega varias carpetas y archivos al proyecto. Para obtener más información acerca de estos archivos, vea [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     En la vista **código fuente** del diseñador de Visual Web Developer, aparece el archivo de paginación ASP.net. Puede diseñar la página agregando controles desde el **cuadro de herramientas** y colocándolos en marcadores de posición de contenido. Para obtener más información, vea [vista Código fuente, diseñador de páginas web](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Si desea controlar los eventos de control, agregue código al archivo de código para la página de la aplicación.

     El archivo de código aparece si expande el nodo del archivo de paginación ASP.NET y tiene una extensión *. CS* o *. VB* , dependiendo del lenguaje del proyecto. Para ver un ejemplo completo de cómo crear una página de aplicación, consulte [Tutorial: crear una página de aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Consulte también
- [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Tutorial: crear una página de aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
