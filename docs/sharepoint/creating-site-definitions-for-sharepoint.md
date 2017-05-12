---
title: "Crear definiciones de sitio para SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, definiciones de sitio"
  - "definiciones de sitio [desarrollo de SharePoint en Visual Studio]"
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Crear definiciones de sitio para SharePoint
  El proyecto Definición de sitios de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] permite crear una *definición de sitio* que sirve como base para un nuevo sitio de SharePoint.  Estas definiciones no solo determinan el aspecto y comportamiento del sitio de SharePoint, sino también el contenido y la funcionalidad predeterminados.  En la definición puede colocar listas preconfiguradas, tipos de contenido, receptores de eventos, imágenes, y otros elementos.  SharePoint incluye algunas definiciones de sitio como BLOG, por ejemplo.  Un sitio que se ha creado basado en la definición de sitio BLOG contiene las listas, los elementos web y otros elementos que requiere un sitio de blogs.  
  
 Para obtener más información sobre las definiciones del sitio, [Plantillas y definiciones del sitio](http://go.microsoft.com/fwlink/?LinkId=179134)vea.  
  
## Proyectos de definición de sitios  
 Los proyectos de definición de sitios de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proporcionan solo los archivos básicos que un sitio de SharePoint necesita; no proporcionan ninguna funcionalidad predeterminada.  Debe agregar los archivos y el contenido para proporcionar la funcionalidad que desea.  Puede compilar el sitio creando y agregando los archivos que necesita manualmente.  
  
## Asociación de características  
 Una ventaja de crear las definiciones de sitios en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] es que utiliza la *Asociación de características* automáticamente.  La asociación de característica adjunta una característica a una definición del sitio en lugar de incrustar su funcionalidad en la propia definición del sitio.  Haciendo esto se puede agregar la característica a cualquier sitio creado utilizando la definición del sitio sin modificar la definición del sitio original.  Para obtener más información, vea [La asociación de característica](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## Componentes del proyecto de definición de sitios  
 Al crear una solución de definición de sitios, los archivos predeterminados siguientes se agregan al nodo **SiteDefinition**.  
  
|Nombre de archivo|Descripción|  
|-----------------------|-----------------|  
|default.aspx|Página principal de ASPX predeterminada para el nuevo sitio de SharePoint.|  
|onet.xml|Especifica la configuración del nuevo sitio, los componentes de la plantilla de definición del sitio y el comportamiento predeterminado.  Esta configuración puede incluir atributos como son los tipos de contenido que están habilitados, las vistas de lista predeterminadas, archivos de plantillas de documentos y elementos web incluidos con el sitio.  De forma predeterminada, la sección `Modules` enumera una lista de los archivos que se van a agregar al sitio de SharePoint y cómo se configuran.|  
|webtemp\_*SiteDefinitionName*.xml|Especifica las configuraciones de definición de sitio que aparecen en la sección **Selección de plantilla** de la página **Nuevo sitio de SharePoint**.|  
  
 De forma predeterminada, todas las definiciones del sitio se almacenan en la carpeta de Servidor Extensions\\14\\TEMPLATE\\SiteTemplates de Files\\Common Files\\Microsoft Shared\\Web de \\Program de *drive:*.  Cada definición del sitio tiene su propia subcarpeta.  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Tutorial: Crear un proyecto de definición de sitio básico](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Ofrece instrucciones paso a paso para crear un proyecto de definición de sitio básico en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Cómo: Cree una definición y una configuración de sitio personalizadas](http://go.microsoft.com/fwlink/?LinkId=183309)|Describe cómo puede crear una definición de sitio personalizada en SharePoint si copia una definición de sitio existente y, a continuación, la modifica.|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|Describe el archivo original que especifica las definiciones de sitio disponibles en la sección **Selección de plantilla** de la página **Nuevo sitio de SharePoint**.|  
|[Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Describe cómo preparar las soluciones de SharePoint para el uso global.|  
|[Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Describe cómo se crean elementos de una página SharePoint que los usuarios puedan modificar.|  
|[Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Describe cómo se crean controles reutilizables que se ejecutan en páginas de aplicación y elementos web.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Describe cómo utilizar el diseñador que aparece al abrir una página web en el proyecto.|  
|[Información general sobre ASP.NET Web pages](http://go.microsoft.com/fwlink/?LinkId=178726)|Proporciona información general sobre la estructura de las páginas web [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], cómo [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] procesa las páginas y cómo las páginas [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] muestran marcado que cumple las normas XHTML.|  
|[Sintaxis de páginas Web de ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Describe los elementos de marcado que constituyen una página ASP.NET.|  
|[Programar ASP.NET Web Pages](http://go.microsoft.com/fwlink/?LinkId=178728)|Proporciona información acerca de cómo crear controladores de eventos en páginas de [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] y cómo trabajar con scripts de cliente.|  
|[Programación en Windows SharePoint services](http://go.microsoft.com/fwlink/?LinkId=178729)|Describe cómo utilizar el modelo de objetos administrado que se proporciona en [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  