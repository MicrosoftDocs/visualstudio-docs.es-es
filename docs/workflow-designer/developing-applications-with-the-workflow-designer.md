---
title: "Desarrollar aplicaciones con el Dise&#241;ador de flujo de trabajo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DefaultWorkflowDesigner"
  - "DefaultWorkflowDesigner.UI"
helpviewer_keywords: 
  - "Diseñador de flujo de trabajo de Visual Studio 2010 [WFD]"
  - "Diseñador de flujo de trabajo de Visual Studio 2010 [WFD], información general"
  - "Diseñador de flujo de trabajo [WFD]"
  - "Diseñador de flujo de trabajo [WFD], información general"
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
caps.handback.revision: 17
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Desarrollar aplicaciones con el Dise&#241;ador de flujo de trabajo
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] es un diseñador visual y un depurador para la creación gráfica y depuración de aplicaciones de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] en el [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] que se hospeda en el entorno de desarrollo de [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Le permite crear una aplicación de flujo de trabajo compuesta, una biblioteca de actividades o un servicio de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] mediante el uso de plantillas y diseñadores de actividades.[!INCLUDE[crabout](../test/includes/crabout_md.md)] los flujos de trabajo, vea [Windows Workflow Foundation](../Topic/Windows%20Workflow%20Foundation.md).  
  
 A continuación se indican diversas características de diseño nuevas que diferencia esta versión nueva de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] de las versiones anteriores de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] se compila utilizando [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)].Esto mejora el uso del diseñador de actividades, así como el rendimiento para flujos de trabajo amplios y complejos.  
  
-   Las actividades personalizadas se diseñan ahora con [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], mediante XAML y se ha simplificado el modelo de programación para crear los diseñadores de actividades.  
  
-   Se ha implementado una actividad de diagrama de flujo, de forma que se puede visualizar el flujo del programa con un estilo de modelado de diagramas de flujo que le resulte familiar.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] cuenta con un nuevo diseñador de variables con el que se pueden declarar variables y establecer su ámbito en de los flujos de trabajo, vinculándolos a las actividades.  
  
-   En [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] proporciona las capacidades íntegras de IntelliSense al crear expresiones Visual Basic en los flujos de trabajo de [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
-   El uso de las capacidades de depuración se amplía ahora a XAML, lo cual hace posible el establecimiento de puntos de interrupción en la definición del flujo de trabajo XAML e ir al código XAML en tiempo de ejecución, que proporciona un uso similar al del código administrado.  
  
-   El hospedar a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se simplifica enormemente si se compara con versiones anteriores y esto requiere ahora unas pocas líneas de código.  
  
-   La nueva actividad <xref:System.Activities.Statements.Flowchart> y su [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md) le permiten visualizar el flujo del programa mediante un estilo de modelado de diagramas de flujo que le resulte familiar.  
  
-   Las actividades de mensajería se han mejorado, lo cual le permite escribir servicios de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] totalmente declarativos \(sin código\).  
  
-   Con la funcionalidad **Agregar referencia de servicio...** se pueden generar automáticamente actividades que tengan acceso a servicios Web.  
  
## En esta sección  
 [Utilizar el Diseñador de flujo de trabajo](../workflow-designer/using-the-workflow-designer.md)  
 Muestra cómo crear nuevas actividades y nuevos proyectos de flujo de trabajo mediante los diseñadores integrados y cómo usar otras herramientas proporcionadas por el diseñador para controlar argumentos, variables, expresiones, importaciones y la ruta de navegación.  
  
 [Utilizar los diseñadores de actividades](../workflow-designer/using-the-activity-designers.md)  
 Describe las categorías de actividades y plantillas, así como sus diseñadores proporcionados por el sistema.  
  
 [Depurar flujos de trabajo con el Diseñador de flujo de trabajo](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Describe cómo realizar procedimientos de depuración tradicionales, así como la depuración de XAML y de expresiones.  
  
 [Ayuda de la interfaz de usuario del Diseñador de flujo de trabajo](../workflow-designer/workflow-designer-ui-help.md)  
 Contiene temas de la Ayuda contextual para los cuadros de diálogo proporcionados por [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], así como indicaciones sobre las características de shell del diseñador, los métodos abreviados de teclado y los mensajes de error.  
  
 [Desarrollar aplicaciones de flujo de trabajo que tienen como destino .NET 3.0 o .NET 3.5 Framework](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Contiene indicaciones sobre el uso del diseñador heredado que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [Rehospedaje del diseñador &#91;WF Samples&#93;](../Topic/Designer%20ReHosting.md)  
 Este ejemplo muestra cómo crear el diseño de WPF para contener el diseñador.  
  
 [Diseñadores de actividad personalizados](../Topic/Custom%20Activity%20Designers.md)  
 Esta sección contiene ejemplos de actividades que utilizan diseñadores personalizados en la presentación en el diseñador de flujo de trabajo.