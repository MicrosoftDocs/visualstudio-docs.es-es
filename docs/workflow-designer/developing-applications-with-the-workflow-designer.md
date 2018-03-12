---
title: "Desarrollo de aplicaciones con el Diseñador de flujo de trabajo | Documentos de Microsoft"
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 75a6fb6eef1f5e8e174607ac141646ab237dd285
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Desarrollar aplicaciones con el Diseñador de flujo de trabajo

El Diseñador de flujo de trabajo de Windows es un diseñador visual y un depurador para la creación gráfica y depuración de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicaciones en el [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] que se hospeda en el [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] entorno de desarrollo. Le permite crear una aplicación de flujo de trabajo compuesta, una biblioteca de actividades o un servicio de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] mediante el uso de plantillas y diseñadores de actividades. Para obtener más información acerca de los flujos de trabajo, consulte la [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

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