---
title: Vistas de flujos de trabajo secuenciales (heredado) | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6b42ba9c1c9f7dbe2beb4a741501967e4968508
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sequential-workflow-views-legacy"></a>Vistas de flujos de trabajo secuenciales (Heredado)
[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] Proporciona un diseñador de flujo de trabajo heredado de Windows que se puede usar al destino la [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] proporciona una manera de crear gráficamente aplicaciones de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] mediante la conocida interfaz de usuario de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] las aplicaciones de flujo de trabajo están formadas por pasos de proceso de flujo de trabajo denominados actividades. Para crear un flujo de trabajo, cree actividades en la superficie de diseño arrastrando sus diseñadores de actividad correspondientes desde **cuadro de herramientas** a la superficie de diseño.

 Cuando se crea un flujo de trabajo secuencial, que es un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), existen tres vistas del flujo de trabajo. Estas vistas son accesibles desde el **flujo de trabajo** menú y en el menú contextual en la superficie de diseño.

 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.

|Opción de menú o pestaña|Descripción|
|----------------------|-----------------|
|**Vista de flujo de trabajo secuencial**|Haga clic en la superficie de diseño y seleccione el **vista flujo de trabajo secuencial** opción en el menú contextual para mostrar el **flujo de trabajo secuencial** vista, que muestra basado en la actividad gráfica representación del flujo de trabajo secuencial. O seleccione **vista flujo de trabajo secuencial** desde el **flujo de trabajo** menú.|
|**Ver controlador de cancelación**|Haga clic en la superficie de diseño y seleccione el **ver controlador de cancelación** opción en el menú contextual para mostrar el **flujo de trabajo secuencial** ver, que muestra la [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) actividad asociada con el flujo de trabajo. O seleccione **ver controlador de cancelación** desde el **flujo de trabajo** menú.|
|**Ver controlador de errores**|Haga clic en la superficie de diseño y seleccione el **ver controlador de errores** opción en el menú contextual para mostrar el **errores** ver, que muestra la [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) actividad asociada con el flujo de trabajo. O seleccione **ver controlador de errores** desde el **flujo de trabajo** menú.|

 Para obtener más información acerca de las vistas similares, consulte [vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Vea también

- [Vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md)
- [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)
- [Modos de creación de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65014)