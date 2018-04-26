---
title: Desarrollar aplicaciones con el Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecc9e42146bfa7de259551ff1c90d27201db5725
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="developing-applications-with-the-workflow-designer"></a>Desarrollar aplicaciones con el Diseñador de flujo de trabajo

El Diseñador de flujo de trabajo de Windows es un diseñador visual y un depurador para la creación gráfica y depuración de aplicaciones de Windows Workflow Foundation (WF) en .NET Framework 4 que se hospeda en el entorno de desarrollo de Visual Studio 2010. Permite crear una aplicación de flujo de trabajo compuesta, la biblioteca de actividades o el servicio de Windows Communication Foundation (WCF) mediante el uso de plantillas y diseñadores de actividad. Para obtener más información acerca de los flujos de trabajo, consulte la [Windows Workflow Foundation &#91;.NET Framework 4&#93;](http://msdn.microsoft.com/Library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Éstos son varias nuevas características de diseño que establecen esta nueva versión del Diseñador de flujo de trabajo además de las versiones anteriores del Diseñador de flujo de trabajo:

-   El Diseñador de flujo de trabajo se basa en Windows Presentation Foundation (WPF). Esto mejora el uso del diseñador de actividades, así como el rendimiento para flujos de trabajo amplios y complejos.

-   Las actividades personalizadas se diseñan ahora con [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], mediante XAML y se ha simplificado el modelo de programación para crear los diseñadores de actividades.

-   Se ha implementado una actividad de diagrama de flujo, de forma que se puede visualizar el flujo del programa con un estilo de modelado de diagramas de flujo que le resulte familiar.

-   El Diseñador de flujo de trabajo tiene un nuevo diseñador de variables que le permite declarar y definir el ámbito de las variables dentro de los flujos de trabajo, vinculándolos a las actividades.

-   En Visual Studio 2010, el Diseñador de flujo de trabajo proporciona capacidades completas de IntelliSense al crear expresiones de Visual Basic en los flujos de trabajo de .NET Framework 4.

-   El uso de las capacidades de depuración se amplía ahora a XAML, lo cual hace posible el establecimiento de puntos de interrupción en la definición del flujo de trabajo XAML e ir al código XAML en tiempo de ejecución, que proporciona un uso similar al del código administrado.

-   Rehospedar el Diseñador de flujo de trabajo fuera de Visual Studio se simplifica en gran medida en comparación con versiones anteriores, requiere ahora unas pocas líneas de código.

-   El nuevo <xref:System.Activities.Statements.Flowchart> actividad y su [Flowchart](../workflow-designer/flowchart-activity-designer.md) le permiten visualizar el flujo del programa con el estilo de modelado de diagrama de flujo familiar.

-   Se han mejorado las actividades de mensajería, lo que le permite escribir totalmente declarativos (sin código) servicios Windows Communication Foundation (WCF).

-   El **Agregar referencia de servicio...**  funcionalidad le permite generar automáticamente actividades que acceder a servicios Web.