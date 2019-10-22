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
ms.openlocfilehash: c7d8a13890814b56865200acf95c8e0565b52b5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655206"
---
# <a name="activity-views-legacy"></a>Vistas de actividad (Heredado)
Muchas de las actividades proporcionadas por [!INCLUDE[wf](../includes/wf-md.md)], a partir de las que se crean flujos de trabajo, disponen de varias vistas de diseño en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Al arrastrar un diseñador de actividad desde el **cuadro de herramientas** a la superficie de diseño y, después, siempre que seleccione la actividad, puede cambiar entre las diferentes vistas de diseño mediante el menú **flujo de trabajo** o haciendo clic con el botón secundario en la opción seleccionada. proceso. Además, si mueve el puntero sobre el nombre de una actividad seleccionada, aparece un conjunto desplegable de pestañas, que puede utilizar para pasar de una vista a otra.

 Cada actividad tiene al menos una vista; Esta es la vista predeterminada que se muestra al arrastrar un diseñador de actividad desde el **cuadro de herramientas** hasta la superficie de diseño. Esta vista predeterminada de la actividad está disponible como la opción **ver [tipo de actividad]** en los menús y la pestaña; por ejemplo, **ver en paralelo**. La mayoría de las actividades tienen vistas adicionales y distintas actividades pueden tener vistas diferentes. Por ejemplo, la actividad [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) tiene la vista compensación y la actividad [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) tiene una vista eventos. Muchas de las actividades que se incluyen en Windows Workflow Foundation tienen vistas de diseño de la **vista cancelar** y **ver los errores** de vista para ver el [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) y un [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociado a ellos.

 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.

|Opción de menú o pestaña|Descripción|
|----------------------|-----------------|
|**Ver [tipo de actividad]**|Seleccione esta opción de menú o pestaña para ver la representación gráfica predeterminada de la actividad seleccionada.|
|**Ver controlador de cancelación**|Seleccione esta opción de menú o pestaña para ver el [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) asociado con la actividad seleccionada.|
|**Ver controlador de errores**|Seleccione esta opción de menú o pestaña para ver el [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociado con la actividad seleccionada.|
|**Ver el controlador de compensación**|Seleccione esta opción de menú o pestaña para ver el [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) asociado con la actividad [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)seleccionada.|
|**Ver controlador de eventos**|Seleccione esta opción de menú o pestaña para ver el [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) asociado al [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)seleccionado.|

 Para obtener información sobre vistas similares, consulte [vistas de flujo de trabajo secuenciales (heredado)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Vea también
 [Vistas de flujo de trabajo secuenciales](../workflow-designer/sequential-workflow-views-legacy.md) de actividades de flujo de trabajo [heredadas](../workflow-designer/legacy-workflow-activities.md)