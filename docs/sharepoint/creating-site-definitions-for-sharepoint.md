---
title: Creación de definiciones de sitio para SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f1a512218c3c1b7af179cfaba3e231a90941fe0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015064"
---
# <a name="create-site-definitions-for-sharepoint"></a>Creación de definiciones de sitio para SharePoint
  El proyecto Definición de sitio de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] le permite crear una *definición de sitio*, que sirve como base para un nuevo sitio de SharePoint. Estas definiciones no solo determinan la apariencia y el comportamiento del sitio de SharePoint, sino también su contenido y funcionalidad predeterminados. En la definición, puede incluir listas preconfiguradas, tipos de contenido, receptores de eventos, imágenes y otros elementos. SharePoint incluye algunas definiciones de sitio, como BLOG, por ejemplo. Cuando se crea un sitio basado en la definición de sitio BLOG, el sitio contiene las listas, los elementos web y otros elementos necesarios para un sitio de blogs.

 Para obtener más información sobre las definiciones de sitio, vea [Plantillas y definiciones de sitio](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Proyectos de definición de sitio
 Los proyectos de definición de sitio de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporcionan solo los archivos básicos necesarios para un sitio de SharePoint; no proporcionan ninguna funcionalidad predeterminada. Tendrá que agregar archivos y contenido para proporcionar la funcionalidad que quiera. Puede compilar el sitio manualmente mediante la creación y adición de los archivos que necesita.

## <a name="feature-stapling"></a>Asociación de características
 Una ventaja de crear definiciones de sitio en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] es que usan la *asociación de características* de forma automática. La asociación de características asocia una característica a una definición de sitio en lugar de insertar su funcionalidad en la propia definición de sitio. Esto le permite agregar la característica a cualquier sitio creado mediante la definición del sitio sin modificar la definición del sitio original. Para obtener más información, vea [Asociación de características](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Componentes de proyectos de definición de sitio
 Cuando se crea una solución de definición de sitio, se agregan los siguientes archivos predeterminados al nodo **SiteDefinition**.

|Nombre de archivo|Descripción|
|---------------|-----------------|
|*default.aspx*|La página principal ASPX predeterminada para el nuevo sitio de SharePoint.|
|*onet.xml*|Especifica la configuración del sitio nuevo, los componentes de la plantilla de definición de sitio y el comportamiento predeterminado. Estos valores pueden incluir atributos como los tipos de contenido que están habilitados, las vistas de lista predeterminadas, los archivos de plantilla de documento y los elementos web que se incluyen con el sitio. De forma predeterminada, en la sección `Modules` se enumeran los archivos que se van a agregar al sitio de SharePoint y cómo se configuran.|
|*webtemp_\<SiteDefinitionName>.xml*|Especifica las configuraciones de definición de sitio que aparecen en la sección **Selección de plantilla** de la página **Nuevo sitio de SharePoint**.|

 De forma predeterminada, todas las definiciones de sitio se almacenan en la carpeta *\<drive:>\Archivos de programa\Archivos comunes\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates*. Cada definición de sitio tiene su propia subcarpeta.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Tutorial: Creación de un proyecto de definición de sitio básico](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Se le guía paso a paso por la creación de un proyecto de definición de sitio básico en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[Cómo: para crear una definición y una configuración de sitio personalizadas](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Se describe cómo crear una definición de sitio personalizada en SharePoint mediante la copia de una definición de sitio existente y la modificación de la copia.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Se describe el archivo original que especifica las definiciones de sitio que aparecen en la sección **Selección de plantilla** de la página **Nuevo sitio de SharePoint**.|
|[Localización de soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Se describe cómo preparar las soluciones de SharePoint para su uso global.|
|[Creación de elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Se describe cómo puede crear partes de una página de SharePoint que los usuarios pueden modificar.|
|[Creación de controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Se describe cómo puede crear controles reutilizables que se ejecutan en páginas de aplicación y elementos web.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Se describe cómo usar el diseñador que aparece al abrir una página web en el proyecto.|
|[Información general de ASP.NET Web Pages](/previous-versions/aspnet/428509ah(v=vs.100))|Se proporciona información general sobre la estructura de las páginas web de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], cómo procesa [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] las páginas y cómo las páginas de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] muestran el marcado que cumple con los estándares XHTML.|
|[Sintaxis de páginas web de ASP.NET](/previous-versions/aspnet/k33801s3(v=vs.100))|Se describen los elementos de marcado que componen una página de ASP.NET.|
|[Programación de ASP.NET Web Pages](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Se proporciona información sobre cómo crear controladores de eventos en páginas de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] y cómo trabajar con scripts de cliente.|
|[Programación en Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Se describe cómo usar el modelo de objetos administrados que se proporciona en [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|

## <a name="see-also"></a>Consulte también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
