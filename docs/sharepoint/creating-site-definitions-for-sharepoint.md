---
title: Crear definiciones de sitio para SharePoint | Documentos de Microsoft
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
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 98be671e456c75c4be79994c84bf1ed6ae5114de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-site-definitions-for-sharepoint"></a>Crear definiciones de sitio para SharePoint
  El proyecto de definición de sitio de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] le permite crear un *definición del sitio*, que sirve como base para un nuevo sitio de SharePoint. Estas definiciones no sólo determinan la apariencia y el comportamiento del sitio de SharePoint, pero también su contenido de forma predeterminada y funcionalidad. En la definición puede colocar listas preconfiguradas, tipos de contenido, receptores de eventos, imágenes y otros elementos. SharePoint incluye algunas definiciones de sitio, como blogs, por ejemplo. Cuando se crea un sitio basado en la definición de sitio BLOG, el sitio contiene las listas, elementos Web y otros elementos que requiere un sitio de blog.  
  
 Para obtener más información acerca de las definiciones de sitio, consulte [plantillas de sitio y las definiciones de](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## <a name="site-definition-projects"></a>Proyectos de definición de sitio  
 En los proyectos de definición de sitio [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporcionan solo los archivos básicos que necesita un sitio de SharePoint; no proporcionan ninguna funcionalidad predeterminada. Debe agregar archivos y el contenido para proporcionar la funcionalidad que desee. Puede crear el sitio manualmente, mediante la creación y agregar los archivos que necesita.  
  
## <a name="feature-stapling"></a>Asociación de características  
 Una ventaja de crear definiciones de sitio en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] es que utilizan automáticamente *característica grapado*. Asociación de característica adjunta una característica a una definición de sitio en lugar de incrustar su funcionalidad en la propia definición de sitio. Esto le permite agregar la característica a cualquier sitio creado mediante el uso de la definición de sitio sin modificar la definición de sitio original. Para obtener más información, consulte [característica grapado](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## <a name="site-definition-project-components"></a>Componentes del proyecto de definición de sitio  
 Cuando se crea una solución de definición de sitio, los siguientes archivos de forma predeterminada se agregan a su **SiteDefinition** nodo.  
  
|Nombre de archivo|Descripción|  
|---------------|-----------------|  
|default.aspx|La página de inicio ASPX predeterminada para el nuevo sitio de SharePoint.|  
|onet.Xml|Especifica la configuración del nuevo sitio, los componentes de la plantilla de definición de sitio y el comportamiento predeterminado. Esta configuración puede incluir atributos como los tipos de contenido que están habilitados, las vistas de lista predeterminadas, archivos de plantilla de documento y elementos que se incluyen con el sitio Web. De forma predeterminada, la `Modules` sección enumeran los archivos que se va a agregar al sitio de SharePoint y cómo están configurados.|  
|webtemp_*SiteDefinitionName*.xml|Especifica las configuraciones de definición de sitio que aparece en el **selección de plantilla** sección de la **nuevo sitio de SharePoint** página.|  
  
 De forma predeterminada, todas las definiciones de sitio se almacenan en la *unidad:*carpeta \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates. Cada definición de sitio tiene su propia subcarpeta.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Tutorial: Crear un proyecto de definición de sitio básico](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Le guía paso a paso para la creación de un proyecto de definición de sitio básico en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Cómo: crear una definición de sitio personalizado y la configuración](http://go.microsoft.com/fwlink/?LinkId=183309)|Describe cómo crear una definición de sitio personalizado en SharePoint copiando una definición de sitio existente y, a continuación, modifica la copia.|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|Describe el archivo original que especifica las definiciones de sitio disponibles en la **selección de plantilla** sección de la **nuevo sitio de SharePoint** página.|  
|[Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Describe cómo preparar las soluciones de SharePoint para su uso global.|  
|[Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Describe cómo puede crear elementos de una página de SharePoint que los usuarios pueden modificar.|  
|[Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Describe cómo puede crear controles reutilizables que se ejecutan en las páginas de aplicación y los elementos Web.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Describe cómo utilizar el diseñador que aparece al abrir una página Web en el proyecto.|  
|[Información general de las páginas Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Proporciona información general sobre la estructura de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas Web, cómo se procesan las páginas por [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]y cómo [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas muestran marcado que cumple con los estándares XHTML.|  
|[Sintaxis de páginas Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Describe los elementos de marcado que constituyen una página ASP.NET.|  
|[Programar páginas Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Proporciona información sobre cómo crear controladores de eventos de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] páginas y cómo trabajar con scripts de cliente.|  
|[Programación en Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Describe cómo utilizar el modelo de objeto administrado que se proporciona en [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  