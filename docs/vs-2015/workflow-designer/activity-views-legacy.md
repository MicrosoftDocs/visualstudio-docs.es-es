---
title: Vistas de actividad (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7546f752ef7ee1053d1b0b785334a8da814720c6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851478"
---
# <a name="activity-views-legacy"></a>Vistas de actividad (Heredado)
Muchas de las actividades proporcionadas por [!INCLUDE[wf](../includes/wf-md.md)], a partir de las que se crean flujos de trabajo, disponen de varias vistas de diseño en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Al arrastrar un diseñador de actividad desde el **cuadro de herramientas** a la superficie de diseño y, después, siempre que seleccione la actividad, puede cambiar entre las diferentes vistas de diseño mediante el menú **flujo de trabajo** o haciendo clic con el botón secundario en la actividad seleccionada. Además, si mueve el puntero sobre el nombre de una actividad seleccionada, aparece un conjunto desplegable de pestañas, que puede utilizar para pasar de una vista a otra.

 Cada actividad tiene al menos una vista; Esta es la vista predeterminada que se muestra al arrastrar un diseñador de actividad desde el **cuadro de herramientas** hasta la superficie de diseño. Esta vista predeterminada de la actividad está disponible como la opción **ver [tipo de actividad]** en los menús y la pestaña; por ejemplo, **ver en paralelo**. La mayoría de las actividades tienen vistas adicionales y distintas actividades pueden tener vistas diferentes. Por ejemplo, la actividad [TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx) tiene la vista compensación y la actividad [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx) tiene una vista eventos. Muchas de las actividades que se incluyen en Windows Workflow Foundation tienen vistas de diseño de la **vista cancelar** y **ver los errores** de vista para ver el [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) y un [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) asociado a ellos.

 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.

|Opción de menú o pestaña|Descripción|
|----------------------|-----------------|
|**Ver [tipo de actividad]**|Seleccione esta opción de menú o pestaña para ver la representación gráfica predeterminada de la actividad seleccionada.|
|**Ver controlador de cancelación**|Seleccione esta opción de menú o pestaña para ver el [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) asociado con la actividad seleccionada.|
|**Ver controlador de errores**|Seleccione esta opción de menú o pestaña para ver el [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) asociado con la actividad seleccionada.|
|**Ver el controlador de compensación**|Seleccione esta opción de menú o pestaña para ver el [CompensationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.compensationhandleractivity.aspx) asociado con la actividad [TransactionScopeActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.transactionscopeactivity.aspx)seleccionada.|
|**Ver controlador de eventos**|Seleccione esta opción de menú o pestaña para ver el [EventHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlersactivity.aspx) asociado al [EventHandlingScopeActivity](https://msdn2.microsoft.com/library/system.workflow.activities.eventhandlingscopeactivity.aspx)seleccionado.|

 Para obtener información sobre vistas similares, consulte [vistas de flujo de trabajo secuenciales (heredado)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Vea también
 [Vistas de flujo de trabajo secuenciales](../workflow-designer/sequential-workflow-views-legacy.md) de actividades de flujo de trabajo [heredadas](../workflow-designer/legacy-workflow-activities.md)
