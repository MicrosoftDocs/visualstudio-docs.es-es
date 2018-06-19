---
title: Diseñador de flujo de trabajo - vistas de actividad (heredado)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d3453ecefece93f593c3d4ebbc261e4332815da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970339"
---
# <a name="activity-views-legacy"></a>Vistas de actividad (Heredado)

Muchas de las actividades proporcionadas por Windows Workflow Foundation (WF), desde el que se componen los flujos de trabajo, tienen varias vistas de diseño disponibles en el Diseñador de flujo de trabajo de Windows heredadas. Al arrastrar un diseñador de actividad de la **cuadro de herramientas** a la superficie de diseño y después cada vez que seleccione la actividad, puede cambiar entre las vistas de diseño diferentes utilizando la **deflujodetrabajo**menú o haciendo clic en la actividad seleccionada. Además, si mueve el puntero sobre el nombre de una actividad seleccionada, aparece un conjunto desplegable de pestañas, que puede utilizar para pasar de una vista a otra.

Cada actividad tiene al menos una vista; se trata de la vista predeterminada que se muestra al arrastrar un diseñador de actividad de la **cuadro de herramientas** a la superficie de diseño. Esta vista predeterminada de actividad está disponible como el **ver [tipo de actividad]** opción en los menús y una pestaña, por ejemplo, **ver Parallel**. La mayoría de las actividades tienen vistas adicionales y distintas actividades pueden tener vistas diferentes. Por ejemplo, el [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) actividad tiene la vista de compensación y la [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) actividad tiene un eventos de vista. Muchas de las actividades que vienen con Windows Workflow Foundation tienen **ver controlador de cancelación** y **ver errores** diseñar vistas para ver el [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) y un [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociados con ellos.

En la tabla siguiente se enumeran el nombre y la descripción de cada vista.

|Opción de menú o pestaña|Descripción|
|----------------------|-----------------|
|**Ver [tipo de actividad]**|Seleccione esta opción de menú o pestaña para ver la representación gráfica predeterminada de la actividad seleccionada.|
|**Ver controlador de cancelación**|Seleccione esta opción de menú o pestaña para ver el [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) asociada a la actividad seleccionada.|
|**Ver controlador de errores**|Seleccione esta opción de menú o pestaña para ver el [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociada a la actividad seleccionada.|
|**Ver controlador de compensación**|Seleccione esta opción de menú o pestaña para ver el [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) asociado seleccionado [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|
|**Ver controlador de eventos**|Seleccione esta opción de menú o pestaña para ver el [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) asociado seleccionado el [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|

Para obtener información acerca de las vistas similares, consulte [vistas de flujo de trabajo secuenciales (heredado)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Vea también

- [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)
- [Vistas de flujos de trabajo secuenciales (heredado)](../workflow-designer/sequential-workflow-views-legacy.md)