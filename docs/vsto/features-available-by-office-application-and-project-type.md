---
title: Características disponibles por tipo de aplicación y el proyecto de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c495119dea17fa7d4a848c6e3d6f5b16128af378
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648157"
---
# <a name="features-available-by-office-application-and-project-type"></a>Características disponibles por tipo de aplicación y el proyecto de Office
  Visual Studio tiene varios tipos de plantillas de proyecto que admiten diferentes escenarios empresariales para las aplicaciones de Microsoft Office, incluyendo los siguientes tipos:  
  
- Personalizaciones de nivel de documento.  
  
- Complementos de VSTO  
  
  No todas las aplicaciones pueden utilizar cada tipo de proyecto. Por ejemplo, los proyectos de nivel de documento solo están disponibles para Microsoft Office Word y Microsoft Office Excel. De forma similar, algunas características solo están disponibles para ciertos tipos de proyectos o aplicaciones. Por ejemplo, el panel de acciones solo está disponible en proyectos de nivel de documento y las extensiones de la Cinta solo están disponibles para algunas aplicaciones. Para obtener más información sobre los diferentes tipos de proyectos, vea [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Las plantillas de proyecto de Office solo están disponibles en algunas ediciones de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulte [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>Tipos de proyecto disponibles para diferentes aplicaciones de Microsoft Office  
 En la siguiente tabla se muestran las aplicaciones que puede utilizar con cada tipo de proyecto.  
  
|Tipos de proyecto|Aplicación de Microsoft Office|  
|-------------------|----------------------------------|  
|Personalizaciones de nivel de documento|Excel<br /><br /> Palabra|  
|Complementos de VSTO|Excel<br /><br /> InfoPath (solo InfoPath 2013 e InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proyecto<br /><br /> Visio<br /><br /> Palabra<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>Características disponibles en diferentes tipos de proyectos  
 En la siguiente tabla se muestra qué tipos de proyecto proporcionan cada característica.  
  
|Característica|Tipos de proyecto que proporcionan la característica|Información adicional|  
|-------------|--------------------------------------------|---------------------|  
|Panel de acciones.|Proyectos de nivel del documento.|[Información general sobre el panel de acciones](../vsto/actions-pane-overview.md)|  
|Implementación ClickOnce|VS y los proyectos de nivel del documento.|[Implementar una solución de Office](../vsto/deploying-an-office-solution.md)|  
|Paneles de tareas personalizados.|Proyectos de complementos de VSTO para las siguientes aplicaciones:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 e InfoPath 2010 solo)<br />-Outlook<br />-PowerPoint<br />-Word|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
|Elementos XML personalizados.|Proyectos de nivel del documento.<br /><br /> Proyectos de nivel de aplicación para las siguientes aplicaciones:<br /><br /> -Excel<br />-PowerPoint<br />-Word|[Información general sobre elementos XML personalizados](../vsto/custom-xml-parts-overview.md)|  
|Caché de datos.|Proyectos de nivel del documento.|[Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)|  
|Exponer un objeto de un complemento de VSTO a otras soluciones de Microsoft Office.|Proyectos de complementos de VSTO.|[Llamar a código en complementos VSTO desde otras soluciones de Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|Los siguientes controles host:<br /><br /> -Gráfico<br />-ListObject<br />-NamedRange<br />: Controles de contenido<br />-Marcador|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO para Word y Excel.|[Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)|  
|Los siguientes controles host:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|Proyectos de nivel del documento.|[Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)|  
|Implementación de varios proyectos.|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO.|[Tutorial: Implementar varias soluciones de Office en un único instalador ClickOnce](https://msdn.microsoft.com/051223c0-4082-4799-b78b-a4763a9def55)|  
|Áreas de formulario de Outlook.|Proyectos de complementos de VSTO para Outlook.|[Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|  
|Acciones posteriores a la implementación.|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO.|[Tutorial: Copiar un documento en el equipo del usuario final después de una instalación ClickOnce](https://msdn.microsoft.com/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Personalizaciones de la Cinta.|Proyectos de nivel del documento.<br /><br /> Proyectos de complementos de VSTO para las siguientes aplicaciones:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 e InfoPath 2010 solo)<br />-Outlook<br />-PowerPoint<br />: Proyecto<br />: Visio<br />-Word|[Información general de la cinta de opciones](../vsto/ribbon-overview.md)|  
|Diseñador de documentos de Visual.|Proyectos de nivel del documento.|[Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>Vea también  
 [Introducción a &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Información general sobre el panel de acciones](../vsto/actions-pane-overview.md)   
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  