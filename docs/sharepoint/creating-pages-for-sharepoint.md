---
title: "Crear páginas para SharePoint | Documentos de Microsoft"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7baa368e34b7b721e7b41c617c6ce6e89bb5f980
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-pages-for-sharepoint"></a>Crear páginas para SharePoint
  Puede crear páginas de aplicación, las páginas del sitio, páginas maestras y diseños de página para un sitio de SharePoint.  
  
 Puede crear páginas de aplicación mediante una plantilla en Visual Studio. Crear páginas de sitio, páginas maestras y diseños de página, mediante el uso de SharePoint Designer. A continuación, puede importar estas páginas en Visual Studio se utilizan en un proyecto de SharePoint.  
  
 También puede modificar la apariencia y el comportamiento de las páginas mediante el uso de hojas de estilos en cascada, temas y ECMAScript.  
  
## <a name="types-of-sharepoint-pages"></a>Tipos de páginas de SharePoint  
 La tabla siguiente describen los cuatro tipos principales de páginas que contiene un sitio de SharePoint.  
  
|Tipo de página.|Descripción|  
|---------------|-----------------|  
|Páginas de aplicación|Crear una página de aplicación si desea que la página para que contenga código personalizado o desea que la página compartir entre varios sitios. En caso contrario, una página del sitio podría ser la mejor opción.|  
|Páginas del sitio|Cree una página del sitio si desea realizar alguna de las siguientes tareas:<br /><br /> -Agregue la página a una biblioteca de SharePoint.<br />-Habilitar la página para que hospede características como elementos Web dinámicos y zonas de elementos Web.<br />-Permitir a los usuarios personalizar la página mediante SharePoint Designer.<br /><br /> No cree una página del sitio si desea que la página para que contenga código personalizado. Aunque puede agregar código personalizado a una página del sitio, el código deja de ejecutarse cuando el usuario personaliza la página mediante el uso de SharePoint Designer.|  
|Páginas maestras|Crear una página maestra si desea definir una estructura común para las páginas del sitio y páginas de aplicación.|  
|Diseños de página|Diseños de página son específicos de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] y permiten definir con más detalle una estructura común para las páginas del sitio y páginas de aplicación.|  
  
 Para obtener información general de cada tipo de página, vea [bloques de creación: páginas y la interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=182095), y [diseños de página y las páginas maestras](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## <a name="creating-application-pages"></a>Crear páginas de aplicación  
 Puede crear páginas de aplicación en Visual Studio mediante la adición de un **página de la aplicación** elemento a un proyecto de SharePoint. Puede agregar controles a la página y, a continuación, controlar eventos de control mediante la adición de código.  
  
 Puede establecer puntos de interrupción en el archivo de código de la página, iniciar al depurador y probar la página en un sitio de SharePoint local sin realizar pasos de configuración adicionales. Para obtener más información, consulte [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## <a name="creating-site-pages-master-pages-and-page-layouts"></a>Creación de páginas del sitio, páginas maestras y diseños de página  
 Puede crear páginas de sitio, páginas maestras y diseños de página mediante SharePoint Designer. A continuación, puede importar estas páginas en Visual Studio. Importe las páginas si desea aprovechar las ventajas de la implementación o las características de control de código fuente que están disponibles en Visual Studio. Para obtener más información, consulte [importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Dado que es difícil de modificar estas páginas después de importarlos, debe diseñar estas páginas antes de importarlos.  
  
## <a name="creating-cascading-style-sheets-ecmascript-and-themes"></a>Creación de temas, ECMAScript y hojas de estilos en cascada  
 Visual Studio no proporciona plantillas para desarrollar hojas de estilos en cascada (CSS), ECMAScript (JavaScript, JScript) o archivos de temas para los sitios de SharePoint. Puede crear estos archivos mediante el uso de las instrucciones disponibles en el SDK de SharePoint o mediante herramientas como SharePoint Designer.  
  
 Puede agregar estos archivos a la solución directamente o puede importarlos. En cualquier caso, debe crear las carpetas asignadas adecuadas para cada elemento que se agrega. Para obtener más información sobre cómo crear una carpeta asignada, vea [Cómo: agregar y quitar carpetas asignado](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Para obtener más información acerca de cómo crear hojas de estilos en cascada, consulte [Cascading Style Sheets Class Usage in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Para obtener más información acerca de cómo crear archivos de JavaScript y JScript para una solución de SharePoint, vea [configuración de seguridad a Basic ASPX Page para ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Para obtener más información acerca de los temas, vea [bloques de creación: páginas y la interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Describe cómo agregar páginas de aplicaciones: contenido de .aspx que se combina con una página maestra de SharePoint.|  
|[Cómo: Crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)|Muestra cómo crear páginas ASP.NET que se ejecutan en un sitio de SharePoint.|  
|[Tutorial: Crear una página de una aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Muestra cómo diseñar y depurar una página Web ASP.NET para un sitio de SharePoint.|  
  
  