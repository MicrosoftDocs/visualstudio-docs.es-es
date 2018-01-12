---
title: "Características disponibles por aplicación y tipo de proyecto Office | Documentos de Microsoft"
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
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b79c7a913e8ce06b1d833f78aad9e8565d54aff2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="features-available-by-office-application-and-project-type"></a>Características disponibles por aplicación y tipo de proyecto de Office
  Visual Studio tiene varios tipos de plantillas de proyecto que admiten diferentes escenarios empresariales para las aplicaciones de Microsoft Office, incluyendo los siguientes tipos:  
  
-   Personalizaciones de nivel de documento.  
  
-   Complementos de VSTO  
  
 No todas las aplicaciones pueden utilizar cada tipo de proyecto. Por ejemplo, los proyectos de nivel de documento solo están disponibles para Microsoft Office Word y Microsoft Office Excel. De forma similar, algunas características solo están disponibles para ciertos tipos de proyectos o aplicaciones. Por ejemplo, el panel de acciones solo está disponible en proyectos de nivel de documento y las extensiones de la Cinta solo están disponibles para algunas aplicaciones. Para obtener más información acerca de los diferentes tipos de proyectos, vea [información general sobre el desarrollo de soluciones de Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Las plantillas de proyecto de Office solo están disponibles en algunas ediciones de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulta [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>Tipos de proyecto disponibles para las diferentes aplicaciones de Microsoft Office  
 En la siguiente tabla se muestran las aplicaciones que puede utilizar con cada tipo de proyecto.  
  
|Tipos de proyecto|Aplicación de Microsoft Office|  
|-------------------|----------------------------------|  
|Personalizaciones de nivel de documento|Excel<br /><br /> Palabra|  
|Complementos de VSTO|Excel<br /><br /> InfoPath (solo InfoPath 2013 e InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proyecto<br /><br /> Visio<br /><br /> Palabra<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>Características disponibles en diferentes tipos de proyectos  
 En la siguiente tabla se muestra qué tipos de proyecto proporcionan cada característica.  
  
|Característica|Tipos de proyecto que proporcionan la característica|Información adicional|  
|-------------|--------------------------------------------|---------------------|  
|Panel de acciones.|Proyectos de nivel del documento.|[Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)|  
|Implementación ClickOnce|VS y los proyectos de nivel del documento.|[Implementación de una solución de Office](../vsto/deploying-an-office-solution.md)|  
|Paneles de tareas personalizados.|Proyectos de complementos de VSTO para las siguientes aplicaciones:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 e InfoPath 2010 solo)<br />-Outlook<br />-PowerPoint<br />-Word|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
|Elementos XML personalizados.|Proyectos de nivel del documento.<br /><br /> Proyectos de nivel de aplicación para las siguientes aplicaciones:<br /><br /> -Excel<br />-PowerPoint<br />-Word|[Información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md)|  
|Caché de datos.|Proyectos de nivel del documento.|[Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)|  
|Exponer un objeto de un complemento de VSTO en otras soluciones de Microsoft Office.|Proyectos de complementos de VSTO.|[Llamar a código en complementos VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|Los siguientes controles host:<br /><br /> : Gráfico<br />-ListObject<br />-NamedRange<br />: Los controles de contenido<br />-Marcador|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO para Word y Excel.|[Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)|  
|Los siguientes controles host:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|Proyectos de nivel del documento.|[Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)|  
|Implementación de varios proyectos.|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO.|[Tutorial: Implementar varias soluciones de Office en un único instalador de ClickOnce](http://msdn.microsoft.com/en-us/051223c0-4082-4799-b78b-a4763a9def55)|  
|Áreas de formulario de Outlook.|Proyectos de complementos de VSTO para Outlook.|[Creación de áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|  
|Acciones posteriores a la implementación.|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO.|[Tutorial: Copiar un documento en el equipo del usuario final después de una instalación de ClickOnce](http://msdn.microsoft.com/en-us/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Personalizaciones de la Cinta.|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO para las siguientes aplicaciones:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 e InfoPath 2010 solo)<br />-Outlook<br />-PowerPoint<br />: Proyecto<br />-Visio<br />-Word|[Información general sobre la cinta](../vsto/ribbon-overview.md)|  
|Diseñador de documentos de Visual.|Proyectos de nivel del documento.|[Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>Vea también  
 [Introducción a &#40; desarrollo de Office en Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)   
 [Implementación de una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  