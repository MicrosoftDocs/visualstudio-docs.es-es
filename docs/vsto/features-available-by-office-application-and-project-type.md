---
title: "Caracter&#237;sticas disponibles por aplicaci&#243;n y tipo de proyecto de Office | Microsoft Docs"
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
helpviewer_keywords: 
  - "complementos [desarrollo de Office en Visual Studio]"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio]"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio]"
  - "áreas de formulario [desarrollo de Office en Visual Studio], características disponibles"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], características disponibles"
  - "desarrollo de Office en Visual Studio, características"
  - "proyectos de Office [desarrollo de Office en Visual Studio], características disponibles"
  - "Cinta [desarrollo de Office en Visual Studio]"
ms.assetid: 3e9aa4d3-affb-4f76-bc67-49fe5f26a6a1
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Caracter&#237;sticas disponibles por aplicaci&#243;n y tipo de proyecto de Office
  Visual Studio tiene varios tipos de plantillas de proyecto que admiten diferentes escenarios empresariales para las aplicaciones de Microsoft Office, incluyendo los siguientes tipos:  
  
-   Personalizaciones de nivel de documento.  
  
-   Complementos de VSTO  
  
 No todas las aplicaciones pueden utilizar cada tipo de proyecto.  Por ejemplo, los proyectos de nivel de documento solo están disponibles para Microsoft Office Word y Microsoft Office Excel.  De forma similar, algunas características solo están disponibles para ciertos tipos de proyectos o aplicaciones.  Por ejemplo, el panel de acciones solo está disponible en proyectos de nivel de documento y las extensiones de la Cinta solo están disponibles para algunas aplicaciones.  Para obtener más información sobre los diferentes tipos de proyectos, vea [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Las plantillas de proyecto de Office solo están disponibles en algunas ediciones de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Para obtener más información, consulte [Configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)  
  
## Tipos de proyecto disponibles para las diferentes aplicaciones de Microsoft Office  
 En la siguiente tabla se muestran las aplicaciones que puede utilizar con cada tipo de proyecto.  
  
|Tipos de proyecto|Aplicación de Microsoft Office|  
|-----------------------|------------------------------------|  
|Personalizaciones de nivel de documento|Excel<br /><br /> Word|  
|Complementos de VSTO|Excel<br /><br /> InfoPath \(solo InfoPath 2013 e InfoPath 2010\)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proyecto<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## Características disponibles en diferentes tipos de proyectos  
 En la siguiente tabla se muestra qué tipos de proyecto proporcionan cada característica.  
  
|Característica|Tipos de proyecto que proporcionan la característica|Información adicional|  
|--------------------|----------------------------------------------------------|---------------------------|  
|Panel de acciones.|Proyectos de nivel del documento.|[Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)|  
|Implementación ClickOnce|VS y los proyectos de nivel del documento.|[Implementar una solución de Office](../vsto/deploying-an-office-solution.md)|  
|Paneles de tareas personalizados.|Proyectos de complementos de VSTO para las siguientes aplicaciones:<br /><br /> -   Excel<br />-   InfoPath \(solo InfoPath 2013 e InfoPath 2010\)<br />-   Outlook<br />-   PowerPoint<br />-   Word|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
|Elementos XML personalizados.|Proyectos de nivel del documento.<br /><br /> Proyectos de nivel de aplicación para las siguientes aplicaciones:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|[Información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md)|  
|Caché de datos.|Proyectos de nivel del documento.|[Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)|  
|Exponer un objeto de un complemento de VSTO en otras soluciones de Microsoft Office.|Proyectos de complementos de VSTO.|[Llamar a código en complementos de VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|Los siguientes controles host:<br /><br /> -   Chart<br />-   ListObject<br />-   NamedRange<br />-   Controles de contenido<br />-   Marcador|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO para Word y Excel.|[Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)|  
|Los siguientes controles host:<br /><br /> -   XMLMappedRange<br />-   XMLNode<br />-   XMLNodes|Proyectos de nivel del documento.|[Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)|  
|Implementación de varios proyectos.|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO.|[Tutorial: Implementar varias soluciones de Office en un instalador de ClickOnce único](http://msdn.microsoft.com/es-es/051223c0-4082-4799-b78b-a4763a9def55)|  
|Áreas de formulario de Outlook.|Proyectos de complementos de VSTO para Outlook.|[Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|  
|Acciones posteriores a la implementación.|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO.|[Tutorial: Copiar un documento en el equipo del usuario final tras una instalación de ClickOnce](http://msdn.microsoft.com/es-es/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Personalizaciones de la Cinta.|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO para las siguientes aplicaciones:<br /><br /> -   Excel<br />-   InfoPath \(solo InfoPath 2013 e InfoPath 2010\)<br />-   Outlook<br />-   PowerPoint<br />-   Proyecto<br />-   Visio<br />-   Word|[Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)|  
|Diseñador de documentos de Visual.|Proyectos de nivel del documento.|[Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## Vea también  
 [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  