---
title: Crear páginas para SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f58af55b18d7cd6341b779d71da2994875c98a62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62419894"
---
# <a name="create-pages-for-sharepoint"></a>Crear páginas para SharePoint
  Puede crear páginas de aplicación, las páginas del sitio, las páginas maestras y diseños de página para un sitio de SharePoint.

 Puede crear páginas de aplicación mediante una plantilla en Visual Studio. Crear páginas del sitio, las páginas maestras y diseños de página mediante SharePoint Designer. A continuación, puede importar estas páginas en Visual Studio para usarlos en un proyecto de SharePoint.

 También puede modificar la apariencia y comportamiento de las páginas mediante el uso de hojas de estilos en cascada, ECMAScript y temas.

## <a name="types-of-sharepoint-pages"></a>Tipos de páginas de SharePoint
 En la tabla siguiente se describe los cuatro tipos principales de las páginas que contiene un sitio de SharePoint.

|Tipo de página|Descripción|
|---------------|-----------------|
|Páginas de aplicación|Crear una página de aplicación si desea que la página para que contenga código personalizado o si desea que la página para compartirse entre varios sitios. En caso contrario, una página del sitio podría ser la mejor opción.|
|Páginas del sitio|Crear una página de sitio si desea realizar cualquiera de las siguientes tareas:<br /><br /> -Agregar la página a una biblioteca de SharePoint.<br />-Habilitar la página a las características de host como elementos Web dinámicos y zonas de elementos Web.<br />-Habilitar a los usuarios personalizar la página mediante SharePoint Designer.<br /><br /> No cree una página de sitio si desea que la página para que contenga código personalizado. Aunque puede agregar código personalizado a una página del sitio, el código deja de ejecutarse cuando el usuario personaliza la página mediante SharePoint Designer.|
|Páginas maestras|Crear una página maestra si desea definir una estructura común para las páginas del sitio y las páginas de aplicación.|
|Diseños de página|Diseños de página son específicos de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] y le permiten definir aún más una estructura común para las páginas del sitio y las páginas de aplicación.|

 Para obtener información general de cada tipo de página, vea [bloques de creación: Las páginas y la interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=182095), y [páginas maestras y diseños de página](http://go.microsoft.com/fwlink/?LinkID=182096).

## <a name="create-application-pages"></a>Crear páginas de aplicación
 Puede crear páginas de aplicación en Visual Studio mediante la adición de un **página aplicación** elemento a un proyecto de SharePoint. Puede agregar controles a la página y, a continuación, controlar eventos de control mediante la adición de código.

 Puede establecer puntos de interrupción en el archivo de código de la página, inicie al depurador y probar la página en un sitio de SharePoint local sin necesidad de realizar los pasos de configuración adicionales. Para obtener más información, consulte [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Crear páginas del sitio, las páginas maestras y diseños de página
 Puede crear páginas del sitio, las páginas maestras y diseños de página mediante SharePoint Designer. A continuación, puede importar estas páginas en Visual Studio. Importe las páginas si desea aprovechar las ventajas de la implementación o las características de control de código fuente que están disponibles en Visual Studio. Para obtener más información, consulte [importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Dado que es difícil de modificar estas páginas después de importarlos, debe diseñar estas páginas antes de importarlos.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Crear hojas de estilos en cascada, ECMAScript y temas
 Visual Studio no proporciona plantillas para desarrollar hojas de estilos en cascada (CSS), ECMAScript (JavaScript y JScript) o archivos de temas para los sitios de SharePoint. Puede crear estos archivos mediante las instrucciones disponibles en el SDK de SharePoint o mediante herramientas como SharePoint Designer.

 Puede agregar estos archivos directamente a la solución o puede importarlos. En cualquier caso, debe crear las carpetas asignadas adecuadas para cada elemento que se agrega. Para obtener más información sobre cómo crear una carpeta asignada, vea [Cómo: agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Para obtener más información acerca de cómo crear hojas de estilos en cascada, consulte [Cascading Style Sheets Class Usage en SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Para obtener más información sobre cómo crear archivos de JavaScript y JScript para una solución de SharePoint, vea [configuración copia unas básica página ASPX para ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099). Para obtener más información acerca de los temas, vea [bloques de creación: Las páginas y la interfaz de usuario](http://go.microsoft.com/fwlink/?LinkID=182095).

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Describe cómo agregar páginas de aplicaciones: *.aspx* contenido que se combina con una página principal de SharePoint.|
|[Cómo: Crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)|Muestra cómo crear páginas ASP.NET que se ejecutan en un sitio de SharePoint.|
|[Tutorial: Crear una página de aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Muestra cómo diseñar y depurar una página Web ASP.NET para un sitio de SharePoint.|
