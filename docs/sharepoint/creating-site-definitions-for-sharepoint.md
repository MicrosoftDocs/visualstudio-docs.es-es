---
title: Crear definiciones de sitio para SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 3b2709426cca892e60d864fa62695b2eef8c776b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874047"
---
# <a name="create-site-definitions-for-sharepoint"></a>Crear definiciones de sitios para SharePoint
  El proyecto de definición de sitio de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] le permite crear un *definición del sitio*, que sirve como base para un nuevo sitio de SharePoint. Estas definiciones no sólo determinan la apariencia y comportamiento del sitio de SharePoint, pero también su contenido de forma predeterminada y funcionalidad. Puede colocar en la definición de listas preconfiguradas, tipos de contenido, receptores de eventos, imágenes y otros elementos. SharePoint incluye algunas definiciones de sitio, como blogs, por ejemplo. Cuando se crea un sitio basado en la definición de sitio BLOG, el sitio contiene las listas, elementos Web y otros elementos que requiere un sitio de blog.  
  
 Para obtener más información acerca de las definiciones de sitio, consulte [plantillas y definiciones](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Proyectos de definición de sitio
 En los proyectos de definición de sitio [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporcionan solo los archivos básicos que necesita un sitio de SharePoint; no proporcionan ninguna funcionalidad de forma predeterminada. Debe agregar los archivos y contenido para proporcionar la funcionalidad que desee. Puede crear el sitio manualmente, mediante la creación y agregar los archivos que necesita.  
  
## <a name="feature-stapling"></a>Grapado de características
 Una ventaja de crear definiciones de sitio en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] es que utilizan automáticamente *característica grapado*. Asociación de característica adjunta una característica a una definición de sitio en lugar de incrustar su funcionalidad en la definición del sitio. Esto le permite agregar la característica a cualquier sitio creado mediante el uso de la definición del sitio sin modificar la definición del sitio original. Para obtener más información, consulte [característica grapado](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Componentes de proyecto de definición de sitio
 Cuando se crea una solución de definición de sitio, los siguientes archivos de forma predeterminada se agregan a su **SiteDefinition** nodo.  
  
|Nombre de archivo|Descripción|  
|---------------|-----------------|  
|*default.aspx*|La página de principal ASPX predeterminada para el nuevo sitio de SharePoint.|  
|*onet.xml*|Especifica la configuración del nuevo sitio, los componentes de la plantilla de definición de sitio y el comportamiento predeterminado. Esta configuración puede incluir atributos como los tipos de contenido que están habilitados, las vistas de lista de forma predeterminada, los archivos de plantilla de documento y los elementos incluidos con el sitio Web. De forma predeterminada, el `Modules` sección enumeran los archivos de agregarse al sitio de SharePoint y cómo están configurados.|  
|*webtemp_\<SiteDefinitionName>.xml*|Especifica las configuraciones de definición de sitio que aparece en el **selección de plantilla** sección de la **nuevo sitio de SharePoint** página.|  
  
 De forma predeterminada, todas las definiciones de sitio se almacenan en el  *\<unidad: > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates* carpeta. Cada definición de sitio tiene su propia subcarpeta.  
  
## <a name="related-topics"></a>Temas relacionados
  
|Título|Descripción|  
|-----------|-----------------|  
|[Tutorial: Crear un proyecto de definición de sitio básico](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Le guía paso a paso para la creación de un proyecto de definición de sitio básico en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Cómo: Crear una definición personalizada del sitio y la configuración](http://go.microsoft.com/fwlink/?LinkId=183309)|Describe cómo crear una definición personalizada del sitio de SharePoint copiando una definición de sitio existente y, a continuación, modifica la copia.|  
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|Describe el archivo original que especifica las definiciones de sitios disponibles en el **selección de plantilla** sección de la **nuevo sitio de SharePoint** página.|  
|[Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Describe cómo preparar las soluciones de SharePoint para su uso global.|  
|[Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Describe cómo puede crear elementos de una página de SharePoint que los usuarios pueden modificar.|  
|[Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Describe cómo puede crear controles reutilizables que se ejecutan en las páginas de aplicación y los elementos Web.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Describe cómo utilizar el diseñador que aparece al abrir una página Web en el proyecto.|  
|[Información general sobre las páginas Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Proporciona información general sobre la estructura de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas Web, cómo se procesan las páginas por [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]y cómo [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] las páginas muestran marcado que cumple con los estándares XHTML.|  
|[Sintaxis de páginas Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Describe los elementos de marcado que constituyen una página ASP.NET.|  
|[Programación de las páginas Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Proporciona información sobre cómo crear controladores de eventos en [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas y cómo trabajar con scripts de cliente.|  
|[Programación en Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Describe cómo utilizar el modelo de objeto administrado que se proporciona en [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>Vea también
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
