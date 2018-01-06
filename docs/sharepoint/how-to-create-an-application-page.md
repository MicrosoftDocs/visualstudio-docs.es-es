---
title: "Cómo: crear una página de aplicación | Documentos de Microsoft"
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 75c896f101f1eb0a11884b492ba559045a1dd180
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-application-page"></a>Cómo: Crear una página de aplicación
  Puede crear una página web ASP.NET para uno o varios sitios de SharePoint. En SharePoint, estas páginas se denominan páginas de aplicación. A diferencia de una página del sitio, una página de aplicación contiene código que se ejecuta detrás de la página. Para obtener más información, consulte [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>Para crear una página de aplicación  
  
1.  En Visual Studio, abra o cree un proyecto de SharePoint.  
  
     Para obtener más información, consulte [proyecto de SharePoint y plantillas de elementos de proyecto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  En el **Explorador de soluciones**, elija el nodo de proyecto.  
  
3.  En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
4.  En el **Agregar nuevo elemento** cuadro de diálogo, expanda el **SharePoint** nodo y, a continuación, elija la **2010** elemento.  
  
5.  En la lista de plantillas de SharePoint, elija **página de la aplicación**.  
  
6.  En el **nombre** cuadro, especifique un nombre para la página de aplicación y, a continuación, elija la **agregar** botón.  
  
     Visual Studio agrega varias carpetas y archivos al proyecto. Para obtener más información acerca de estos archivos, consulte [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     En el **origen** aparece la vista del Diseñador de Visual Web Developer, el archivo de paginación ASP.NET. Puede diseñar la página agregando controles desde el **cuadro de herramientas** y colocarlas en marcadores de posición de contenido. Para obtener más información, consulte [vista código fuente, Diseñador de páginas Web](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Si desea controlar los eventos de control, agregue código al archivo de código para la página de aplicación.  
  
     El archivo de código aparece si expande el nodo para el archivo de paginación ASP.NET y tiene una extensión .cs o .vb, según el lenguaje del proyecto. Para obtener un ejemplo de extremo a extremo de creación de una página de aplicación, consulte [Tutorial: crear una página de aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Tutorial: Crear una página de una aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  