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
ms.openlocfilehash: 47f403f4eec6ec66563ae88bec226e073f625716
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981096"
---
# <a name="create-application-pages-for-sharepoint"></a>Crear páginas de aplicación para SharePoint
  Una *Página de aplicación* es una página web de ASP.net diseñada para su uso en un sitio web de SharePoint. Las páginas de aplicación son un tipo especializado de página de ASP.NET. La principal diferencia entre una página de aplicación y una página de ASP.NET estándar es que una página de aplicación contiene contenido que se combina con una página maestra de SharePoint. Una página maestra permite que las páginas de aplicación compartan la misma apariencia y comportamiento que las demás páginas de un sitio.

 Visual Studio le permite diseñar páginas de aplicación mediante un diseñador. El diseñador muestra un área de contenido para cada marcador de posición de contenido que se define en una página maestra. Puede diseñar la página de la aplicación arrastrando los controles a estas áreas de contenido.

## <a name="application-pages"></a>Páginas de aplicación
 Las páginas de aplicación se comparten entre todos los sitios del servidor, mientras que una página del sitio es específica de un sitio. Para obtener más información, los [tipos de páginas de SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

 De forma predeterminada, la mayoría de las páginas que aparecen al crear un sitio de SharePoint son páginas del sitio. Se puede Agregar una página de sitio a una biblioteca de páginas de SharePoint. Los usuarios pueden personalizar una página del sitio mediante herramientas como SharePoint Designer. Una página de sitio también puede hospedar características como elementos web dinámicas y zonas de elementos Web.

 Las páginas de aplicación no pueden realizar estas acciones. Sin embargo, una página de aplicación es el mejor tipo de página que se va a crear si desea que la página contenga código personalizado. Aunque puede agregar código personalizado a una página de sitio, el código deja de ejecutarse cuando el usuario Personaliza la página mediante herramientas como SharePoint Designer.

> [!NOTE]
> Visual Studio no proporciona plantillas que le ayuden a crear páginas de sitio para un sitio de SharePoint. Para obtener más información, vea [tipos de páginas de SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

## <a name="create-an-application-page"></a>Crear una página de aplicación
 Para crear una página de aplicación, agregue un elemento de **Página de aplicación** a un proyecto de SharePoint. Cuando se crea una página de aplicación, Visual Studio agrega las siguientes carpetas al proyecto:

|Carpeta|Descripción|
|------------|-----------------|
|Diseños|Se asigna al directorio virtual de _ layouts del sistema de archivos de SharePoint.|
|Carpeta Layouts|Contiene los archivos que componen la página de la aplicación. De forma predeterminada, esta carpeta tiene el mismo nombre que el proyecto. Puede cambiar el nombre de esta carpeta en cualquier momento. Al ejecutar el proyecto, Visual Studio implementa esta carpeta en el directorio virtual _ layouts del sistema de archivos de SharePoint.|

 Visual Studio agrega los siguientes archivos al proyecto:

|Archivo|Descripción|
|----------|-----------------|
|Archivo de paginación ASP.NET (*. aspx*)|Contiene el marcado XML que define la página.|
|Archivo de código de página de aplicación|Contiene código subyacente a la página de la aplicación. Agregue código que controle los eventos a este archivo.|
|Archivo de código del diseñador de páginas de aplicación|Contiene código generado por el diseñador. No edite directamente este archivo.|

## <a name="design-and-debug-an-application-page"></a>Diseño y depuración de una página de aplicación
 Diseñe el contenido de una página de aplicación mediante la vista de diseñador de Visual Studio. Este diseñador aparece al abrir la página de aplicación en el proyecto (haciendo doble clic en él o abriendo su menú contextual y, a continuación, eligiendo **abrir**) y, a continuación, elija el botón **diseño** situado en la parte inferior del editor.

> [!NOTE]
> Solo puede diseñar la página en la vista **código fuente** del diseñador. La vista de **diseño** del diseñador está deshabilitada para las páginas de la aplicación.

 Puede depurar una página de aplicación del mismo modo que depuraría otros elementos de proyecto de SharePoint en Visual Studio. Al iniciar el depurador de Visual Studio, Visual Studio abre el sitio de SharePoint.

 Para ver la página de la aplicación, debe navegar manualmente hasta la ubicación de la página de la aplicación (por ejemplo: http://<em>Server_Name</em>/_Layouts/*Project_Name*/ApplicationPage1.aspx).

 Para obtener más información sobre cómo depurar proyectos de SharePoint, vea [solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Elegir una página maestra
 De forma predeterminada, un elemento de **Página de aplicación** hace referencia a la página maestra del sitio que está usando para depurar el proyecto. Esa página se denomina V4. Master y puede encontrarla en la **Galería de páginas maestras** del sitio de SharePoint.

 Puede cambiar explícitamente qué página maestra utiliza la página de la aplicación estableciendo el atributo `MasterPageFile` del elemento `Page` de la aplicación. (Por ejemplo: `MasterPageFile="~/_layouts/applicationv4.master"`). De hecho, debe establecer este atributo si las páginas maestras dinámicas no están habilitadas en el servidor de SharePoint. Para obtener más información acerca de las páginas maestras en SharePoint, vea [Master pages](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14)).

## <a name="see-also"></a>Vea también
- [Desarrollo en SharePoint Foundation en profundidad](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [Información general de ASP.NET](/aspnet/overview)
- [ASP.NET Web Pages](/aspnet/web-pages/index) (Más información sobre páginas web de ASP.NET)
