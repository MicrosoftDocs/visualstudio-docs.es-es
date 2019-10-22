---
title: Crear páginas de aplicación para SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8ac9340ea853a1852d039f05a3ecbb100845ab84
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443541"
---
# <a name="create-application-pages-for-sharepoint"></a>Crear páginas de aplicación para SharePoint
  Un *página aplicación* es una página Web ASP.NET que está diseñada para su uso en un sitio Web de SharePoint. Páginas de aplicación son un tipo especializado de página ASP.NET. La diferencia principal entre una página de aplicación y una página ASP.NET estándar es que una página de aplicación contiene contenido que se combina con una página principal de SharePoint. Páginas de aplicación para compartir el mismo aspecto y comportamiento de otras páginas de un sitio permite que una página maestra.

 Visual Studio le permite diseñar páginas de aplicación utilizando un diseñador. El diseñador muestra un área de contenido para cada marcador de posición de contenido que se define en una página maestra. Puede diseñar la página de aplicación arrastrando controles a estas áreas de contenido.

## <a name="application-pages"></a>Páginas de aplicación
 Las páginas de aplicación se comparten entre todos los sitios en el servidor, mientras que una página del sitio es específica para un sitio. Para obtener más información, [tipos de páginas de SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).

 De forma predeterminada, la mayoría de las páginas que aparecen al crear un sitio de SharePoint son las páginas del sitio. Una página de sitio se puede agregar a una biblioteca de la página de SharePoint. Los usuarios pueden personalizar una página de sitio mediante herramientas como SharePoint Designer. Una página de sitio también puede hospedar características como los elementos Web dinámicos y zonas de elementos Web.

 Las páginas de aplicación no pueden hacer estas cosas. Sin embargo, una página de aplicación es el mejor tipo de página para crear si desea que la página para que contenga código personalizado. Aunque puede agregar código personalizado a una página del sitio, el código deja de ejecutarse cuando el usuario personaliza la página utilizando herramientas como SharePoint Designer.

> [!NOTE]
> Visual Studio no proporciona plantillas que le ayudarán a crear páginas del sitio para un sitio de SharePoint. Para obtener más información, consulte [tipos de páginas de SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).

## <a name="create-an-application-page"></a>Crear una página de aplicación
 Para crear una página de aplicación, agregue un **página aplicación** elemento a un proyecto de SharePoint. Cuando se crea una página de aplicación, Visual Studio agrega las siguientes carpetas al proyecto:

|Carpeta|Descripción|
|------------|-----------------|
|Diseños|Se asigna al directorio virtual _layouts del sistema de archivos de SharePoint.|
|Subcarpeta de diseños|Contiene los archivos que componen la página de aplicación. De forma predeterminada, esta carpeta tiene el mismo nombre que el proyecto. Puede cambiar el nombre de esta carpeta en cualquier momento. Al ejecutar el proyecto, Visual Studio implementa esta carpeta en el directorio virtual _layouts del sistema de archivos de SharePoint.|

 Visual Studio agrega los siguientes archivos al proyecto:

|Archivo|Descripción|
|----------|-----------------|
|Archivo de paginación ASP.NET (*.aspx*)|Contiene el marcado XML que define la página.|
|Archivo de código de página de aplicación|Contiene el código subyacente de la página de aplicación. Agregue código que controla los eventos a este archivo.|
|Archivo de código del Diseñador de página de aplicación|Contiene código generado por el diseñador. No modifique este archivo directamente.|

## <a name="design-and-debug-an-application-page"></a>Diseñar y depurar una página de aplicación
 Diseñar el contenido de una página de aplicación mediante la vista del diseñador en Visual Studio. Este diseñador aparece al abrir la página de aplicación en el proyecto (haciendo doble clic en él o abriendo su menú contextual y, a continuación, eligiendo **abrir**) y, a continuación, elija el **diseño** situado en la parte inferior de el editor.

> [!NOTE]
> Puede diseñar la página solo en el **origen** la vista del diseñador. El **diseño** la vista del diseñador está deshabilitada para las páginas de aplicación.

 Puede depurar una página de aplicación como haría depurar otros elementos de proyecto de SharePoint en Visual Studio. Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.

 Para ver la página de aplicación, debe navegar manualmente a la ubicación de la página de aplicación (por ejemplo: http://<em>nombre_servidor</em>/_layouts /*Project_Name*  /ApplicationPage1.aspx).

 Para obtener más información sobre cómo se depuran proyectos de SharePoint, vea [soluciones de SharePoint de la solución de problemas de](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Elegir una página maestra
 De forma predeterminada, un **página aplicación** elemento hace referencia a la página principal del sitio que está usando para depurar el proyecto. Que la página se denomina v4.master y puede encontrarlo enumerados en el **Galería de páginas maestras** del sitio de SharePoint.

 Puede cambiar a la página maestra que es utilizada por la página de aplicación estableciendo explícitamente el `MasterPageFile` atributo de la aplicación `Page` elemento. (Por ejemplo: `MasterPageFile="~/_layouts/applicationv4.master"`). De hecho, debe establecer este atributo si páginas maestra dinámicas no están habilitadas en el servidor de SharePoint. Para obtener más información acerca de las páginas maestras en SharePoint, vea [páginas maestras](http://go.microsoft.com/fwlink/?LinkID=169281).

## <a name="see-also"></a>Vea también
- [Desarrollo de SharePoint Foundation en profundidad](http://go.microsoft.com/fwlink/?LinkID=182103)
- [Información general de ASP.NET](/aspnet/overview)
- [ASP.NET Web Pages](/aspnet/web-pages/index) (Más información sobre páginas web de ASP.NET)
