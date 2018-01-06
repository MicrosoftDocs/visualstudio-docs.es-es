---
title: "Desarrollo de aplicaciones con el Diseñador de flujo de trabajo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: "17"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 61d58b172c185a908a6314664ccd4cfe2172dc8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="developing-applications-with-the-workflow-designer"></a>Desarrollar aplicaciones con el Diseñador de flujo de trabajo
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] es un diseñador visual y un depurador para la creación gráfica y depuración de aplicaciones de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] en el [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] que se hospeda en el entorno de desarrollo de [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Le permite crear una aplicación de flujo de trabajo compuesta, una biblioteca de actividades o un servicio de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] mediante el uso de plantillas y diseñadores de actividades. [!INCLUDE[crabout](../test/includes/crabout_md.md)]flujos de trabajo, consulte el [Windows Workflow Foundation &#91;. .NET Framework 4 &#93; ](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).  
  
 A continuación se indican diversas características de diseño nuevas que diferencia esta versión nueva de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] de las versiones anteriores de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] se compila utilizando [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]. Esto mejora el uso del diseñador de actividades, así como el rendimiento para flujos de trabajo amplios y complejos.  
  
-   Las actividades personalizadas se diseñan ahora con [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], mediante XAML y se ha simplificado el modelo de programación para crear los diseñadores de actividades.  
  
-   Se ha implementado una actividad de diagrama de flujo, de forma que se puede visualizar el flujo del programa con un estilo de modelado de diagramas de flujo que le resulte familiar.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] cuenta con un nuevo diseñador de variables con el que se pueden declarar variables y establecer su ámbito en de los flujos de trabajo, vinculándolos a las actividades.  
  
-   En [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] proporciona las capacidades íntegras de IntelliSense al crear expresiones Visual Basic en los flujos de trabajo de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
-   El uso de las capacidades de depuración se amplía ahora a XAML, lo cual hace posible el establecimiento de puntos de interrupción en la definición del flujo de trabajo XAML e ir al código XAML en tiempo de ejecución, que proporciona un uso similar al del código administrado.  
  
-   El hospedar a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se simplifica enormemente si se compara con versiones anteriores y esto requiere ahora unas pocas líneas de código.  
  
-   El nuevo <xref:System.Activities.Statements.Flowchart> actividad y su [Flowchart](../workflow-designer/flowchart-activity-designer.md) le permiten visualizar el flujo del programa con el estilo de modelado de diagrama de flujo familiar.  
  
-   Las actividades de mensajería se han mejorado, lo cual le permite escribir servicios de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] totalmente declarativos (sin código).  
  
-   El **Agregar referencia de servicio...**  funcionalidad le permite generar automáticamente actividades que acceder a servicios Web.  
  
## <a name="in-this-section"></a>En esta sección  
 [Usar el Diseñador de flujo de trabajo](../workflow-designer/using-the-workflow-designer.md)  
 Muestra cómo crear nuevas actividades y nuevos proyectos de flujo de trabajo mediante los diseñadores integrados y cómo usar otras herramientas proporcionadas por el diseñador para controlar argumentos, variables, expresiones, importaciones y la ruta de navegación.  
  
 [Usar los diseñadores de actividad](../workflow-designer/using-the-activity-designers.md)  
 Describe las categorías de actividades y plantillas, así como sus diseñadores proporcionados por el sistema.  
  
 [Depurar flujos de trabajo con el Diseñador de flujo de trabajo](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Describe cómo realizar procedimientos de depuración tradicionales, así como la depuración de XAML y de expresiones.  
  
 [Ayuda de la interfaz de usuario del Diseñador de flujo de trabajo](../workflow-designer/workflow-designer-ui-help.md)  
 Contiene temas de la Ayuda contextual para los cuadros de diálogo proporcionados por [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], así como indicaciones sobre las características de shell del diseñador, los métodos abreviados de teclado y los mensajes de error.  
  
 [Desarrollar aplicaciones de flujo de trabajo que tienen como destino .NET 3.0 o .NET 3.5 Framework](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Contiene indicaciones sobre el uso del diseñador heredado que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [Rehospedaje del diseñador &#91; Ejemplos de WF &#93;](http://msdn.microsoft.com/Library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d)  
 Este ejemplo muestra cómo crear el diseño de WPF para contener el diseñador.  
  
 [Diseñadores de actividad personalizados](/dotnet/framework/windows-workflow-foundation/samples/custom-activity-designers)  
 Esta sección contiene ejemplos de actividades que utilizan diseñadores personalizados en la presentación en el diseñador de flujo de trabajo.