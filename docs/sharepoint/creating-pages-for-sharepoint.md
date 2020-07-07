---
title: Crear páginas para SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: 942891bc9281c07966160ea9df065408fcbfd5ff
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015164"
---
# <a name="create-pages-for-sharepoint"></a>Crear páginas para SharePoint
  Puede crear páginas de aplicación, páginas de sitio, páginas maestras y diseños de página para un sitio de SharePoint.

 Puede crear páginas de aplicación mediante una plantilla en Visual Studio. Cree páginas de sitio, páginas maestras y diseños de página con SharePoint Designer. Después, puede importar estas páginas en Visual Studio para usarlas en un proyecto de SharePoint.

 También puede modificar la apariencia y el comportamiento de las páginas mediante hojas de estilos en cascada, ECMAScript y temas.

## <a name="types-of-sharepoint-pages"></a>Tipos de páginas de SharePoint
 En la tabla siguiente se describen los cuatro tipos principales de páginas que contiene un sitio de SharePoint.

|Tipo de página|Descripción|
|---------------|-----------------|
|Páginas de aplicación|Cree una página de aplicación si desea que la página contenga código personalizado o desee que la página se comparta entre varios sitios. De lo contrario, una página de sitio podría ser la mejor opción.|
|Páginas del sitio|Cree una página de sitio si desea realizar alguna de las siguientes tareas:<br /><br /> -Agregar la página a una biblioteca de SharePoint.<br />-Habilite la página para hospedar características como elementos web dinámicas y zonas de elementos Web.<br />-Permitir a los usuarios personalizar la página con SharePoint Designer.<br /><br /> No cree una página de sitio si desea que la página contenga código personalizado. Aunque puede agregar código personalizado a una página de sitio, el código deja de ejecutarse cuando el usuario Personaliza la página con SharePoint Designer.|
|Páginas maestras|Cree una página maestra si desea definir una estructura común para las páginas de sitio y las páginas de aplicación.|
|Diseños de página|Los diseños de página son específicos de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] y permiten definir aún más una estructura común para las páginas del sitio y las páginas de aplicación.|

 Para obtener información general sobre cada tipo de página, vea [bloque de creación: páginas y la interfaz de usuario](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)), así como diseños de [página y páginas maestras](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Crear páginas de aplicación
 Puede crear páginas de aplicación en Visual Studio agregando un elemento de **Página de aplicación** a un proyecto de SharePoint. Puede Agregar controles a la página y, a continuación, controlar los eventos de control agregando código.

 Puede establecer puntos de interrupción en el archivo de código de la página, iniciar el depurador y probar la página en un sitio de SharePoint local sin realizar ningún paso de configuración adicional. Para obtener más información, vea [crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Crear páginas de sitio, páginas maestras y diseños de página
 Puede crear páginas de sitio, páginas maestras y diseños de página con SharePoint Designer. Después, puede importar estas páginas a Visual Studio. Importe las páginas si desea aprovechar las características de implementación o control de código fuente que están disponibles en Visual Studio. Para obtener más información, vea [importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Dado que es difícil modificar estas páginas después de importarlas, debe diseñar estas páginas antes de importarlas.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Crear hojas de estilos en cascada, ECMAScript y temas
 Visual Studio no proporciona plantillas para desarrollar Hojas de estilo CSS (CSS), ECMAScript (JavaScript, JScript) o archivos de tema para los sitios de SharePoint. Puede crear estos archivos mediante las instrucciones disponibles en el SDK de SharePoint o mediante herramientas como SharePoint Designer.

 Puede agregar estos archivos a la solución directamente o puede importarlos. En cualquier caso, debe crear las carpetas asignadas adecuadas para cada elemento que agregue. Para obtener más información acerca de cómo crear una carpeta asignada, consulte [Cómo: agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Para obtener más información sobre la creación de Hojas de estilo CSS, vea [hojas de estilo CSS uso de clases en SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Para obtener más información sobre cómo crear archivos de JavaScript y JScript para una solución de SharePoint, vea [configurar una página aspx básica para ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Para obtener más información sobre los temas, vea [bloque de creación: páginas y la interfaz de usuario](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Describe cómo agregar páginas de aplicaciones: contenido *. aspx* que se combina con una página maestra de SharePoint.|
|[Cómo: crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)|Muestra cómo crear páginas ASP.NET que se ejecutan en un sitio de SharePoint.|
|[Tutorial: crear una página de aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Muestra cómo diseñar y depurar una página web de ASP.NET para un sitio de SharePoint.|
