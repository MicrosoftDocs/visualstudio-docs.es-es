---
title: Creación de páginas para SharePoint | Microsoft Docs
description: Cree páginas de aplicación para SharePoint mediante una plantilla en Visual Studio. Cree páginas del sitio, páginas maestras y diseños de página con SharePoint Designer.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 702d2c4d5cafd6f4ff4ef2e4104da9f6cc02c5fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949173"
---
# <a name="create-pages-for-sharepoint"></a>Creación de páginas para SharePoint
  Puede crear páginas de aplicación, de sitio, maestras y diseños de página para un sitio de SharePoint.

 Puede crear páginas de aplicación mediante una plantilla en Visual Studio. Cree páginas del sitio, páginas maestras y diseños de página con SharePoint Designer. Después, puede importar estas páginas en Visual Studio para usarlas en un proyecto de SharePoint.

 También puede modificar la apariencia y el comportamiento de las páginas mediante hojas de estilos en cascada, ECMAScript y temas.

## <a name="types-of-sharepoint-pages"></a>Tipos de páginas de SharePoint
 En la tabla siguiente se describen los cuatro tipos principales de páginas que contiene un sitio de SharePoint.

|Tipo de página|Descripción|
|---------------|-----------------|
|Páginas de aplicación|Cree una página de aplicación si quiere que la página contenga código personalizado o que se comparta entre varios sitios. De lo contrario, una página del sitio podría ser la mejor opción.|
|Páginas del sitio|Cree una página del sitio si quiere realizar alguna de las tareas siguientes:<br /><br /> - Agregar la página a una biblioteca de SharePoint.<br />- Habilitar la página para hospedar características como Elementos web dinámicos y Zonas de elementos web.<br />- Permitir a los usuarios personalizar la página mediante SharePoint Designer.<br /><br /> No cree una página del sitio si quiere que contenga código personalizado. Aunque puede agregar código personalizado a una página del sitio, el código deja de ejecutarse cuando el usuario personaliza la página mediante SharePoint Designer.|
|Páginas maestras|Cree una página maestra si quiere definir una estructura común para las páginas del sitio y las de aplicación.|
|Diseños de página|Los diseños de página son específicos de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] y permiten definir una estructura común para las páginas del sitio y las de aplicación.|

 Para obtener información general sobre cada tipo de página, vea [Bloque de creación: páginas e interfaz de usuario](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) y [Diseños de página y páginas maestras](/previous-versions/office/developer/sharepoint-2010/ms543497(v=office.14)).

## <a name="create-application-pages"></a>Creación de páginas de aplicación
 Puede crear páginas de aplicación en Visual Studio si agrega un elemento **Página de aplicación** a un proyecto de SharePoint. Puede agregar controles a la página y, después, controlar los eventos de control mediante la adición de código.

 Puede establecer puntos de interrupción en el archivo de código de la página, iniciar el depurador y probar la página en un sitio de SharePoint local sin necesidad de pasos de configuración adicionales. Para obtener más información, vea [Creación de páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

## <a name="create-site-pages-master-pages-and-page-layouts"></a>Creación de páginas del sitio, páginas maestras y diseños de página
 Puede crear páginas del sitio, páginas maestras y diseños de página con SharePoint Designer. Después, puede importar estas páginas a Visual Studio. Importe las páginas si quiere aprovechar las características de implementación o control de código fuente que están disponibles en Visual Studio. Para obtener más información, vea [Importación de elementos desde un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

 Como es difícil modificar estas páginas después de importarlas, debe diseñarlas antes.

## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Creación de hojas de estilo CSS, ECMAScript y temas
 Visual Studio no proporciona plantillas para desarrollar Hojas de estilo CSS (CSS), ECMAScript (JavaScript, JScript) ni archivos de tema para los sitios de SharePoint. Puede crear estos archivos mediante las instrucciones disponibles en el SDK de SharePoint, o bien con herramientas como SharePoint Designer.

 Puede agregar estos archivos a la solución directamente o puede importarlos. En cualquier caso, debe crear las carpetas asignadas adecuadas para cada elemento que agregue. Para obtener más información sobre cómo crear una carpeta asignada, vea [Procedimiento para agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Para obtener más información sobre la creación de hojas de estilo CSS, vea [Uso de clases de hojas de estilo CSS en SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms438349(v=office.14)). Para obtener más información sobre cómo crear archivos de JavaScript y JScript para una solución de SharePoint, vea [Configuración de una página ASPX básica para ECMAScript](/previous-versions/office/developer/sharepoint-2010/ee535709(v=office.14)). Para obtener más información sobre los temas, vea [Bloque de creación: páginas e interfaz de usuario](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Creación de páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Se describe cómo agregar páginas de aplicaciones: contenido de *.aspx* que se combina con una página maestra de SharePoint.|
|[Cómo: para crear una página de aplicación](../sharepoint/how-to-create-an-application-page.md)|Se muestra cómo crear páginas ASP.NET que se ejecutan en un sitio de SharePoint.|
|[Tutorial: Creación de una página de aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Se muestra cómo diseñar y depurar una página web de ASP.NET para un sitio de SharePoint.|
