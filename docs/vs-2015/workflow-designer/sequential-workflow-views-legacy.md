---
title: Vistas de flujo de trabajo secuenciales (heredadas) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76d357c1f6ebc770d0e625e60bae237e37e0a6aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846217"
---
# <a name="sequential-workflow-views-legacy"></a>Vistas de flujos de trabajo secuenciales (Heredado)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] proporciona un heredado [!INCLUDE[wfd1](../includes/wfd1-md.md)] que se puede usar para tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] proporciona una manera de crear gráficamente aplicaciones de [!INCLUDE[wf](../includes/wf-md.md)] mediante la conocida interfaz de usuario de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[wf](../includes/wf-md.md)] las aplicaciones de flujo de trabajo están formadas por pasos de proceso de flujo de trabajo denominados actividades. Para crear un flujo de trabajo, cree actividades en la superficie de diseño arrastrando sus diseñadores de actividad respectivos desde el **cuadro de herramientas** hasta la superficie de diseño.

 Cuando se crea un flujo de trabajo secuencial, que es un [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx), están disponibles tres vistas del flujo de trabajo. Estas vistas son accesibles desde el menú **flujo de trabajo** y desde el menú contextual en la superficie de diseño.

 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.

|Opción de menú o pestaña|Descripción|
|----------------------|-----------------|
|**Ver Flujo de trabajo secuencial**|Haga clic con el botón secundario en la superficie de diseño y seleccione la opción **Ver SequentialWorkflow** en el menú contextual para mostrar la vista **flujo de trabajo secuencial** , que muestra la representación gráfica basada en actividad del flujo de trabajo secuencial. O bien, seleccione **Ver SequentialWorkflow** en el menú **flujo de trabajo** .|
|**Ver controlador de cancelación**|Haga clic con el botón secundario en la superficie de diseño y seleccione la opción **Ver controlador de cancelación** en el menú contextual para mostrar la vista **flujo de trabajo secuencial** , que muestra la actividad [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) asociada al flujo de trabajo. O bien, seleccione **Ver controlador de cancelación** en el menú **flujo de trabajo** .|
|**Ver controlador de errores**|Haga clic con el botón secundario en la superficie de diseño y seleccione la opción **Ver controlador de errores** en el menú contextual para mostrar la vista **errores** , que muestra la actividad [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) asociada al flujo de trabajo. O bien, seleccione **Ver controlador de errores** en el menú **flujo de trabajo** .|

 Para obtener más información sobre vistas similares, consulte [vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Consulte también
 [Vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md) [creación de proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md) [modos de creación de flujos](https://msdn2.microsoft.com/library/bb628440.aspx) de trabajo
