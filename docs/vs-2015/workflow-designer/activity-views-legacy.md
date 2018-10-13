---
title: Vistas de actividad (heredado) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e5fb8368228118b210865b1a351d12b1b5da4b27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229322"
---
# <a name="activity-views-legacy"></a>Vistas de actividad (Heredado)
Muchas de las actividades proporcionadas por [!INCLUDE[wf](../includes/wf-md.md)], a partir de las que se crean flujos de trabajo, disponen de varias vistas de diseño en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Al arrastrar un diseñador de actividad de la **cuadro de herramientas** a la superficie de diseño y, a partir de entonces cada vez que seleccione la actividad, puede cambiar entre las vistas de diseño diferentes mediante el uso del **deflujodetrabajo**menú o hacer clic en la actividad seleccionada. Además, si mueve el puntero sobre el nombre de una actividad seleccionada, aparece un conjunto desplegable de pestañas, que puede utilizar para pasar de una vista a otra.  
  
 Cada actividad tiene al menos una vista; se trata de la vista predeterminada mostrada cuando se arrastra un diseñador de actividad desde la **cuadro de herramientas** a la superficie de diseño. Esta vista predeterminada de actividad está disponible como la **ver [tipo de actividad]** opción en los menús y la pestaña, por ejemplo, **ver Parallel**. La mayoría de las actividades tienen vistas adicionales y distintas actividades pueden tener vistas diferentes. Por ejemplo, el [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) actividad tiene la vista de compensación y la [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) actividad tiene eventos de vista. Muchas de las actividades que vienen con Windows Workflow Foundation tienen **ver controlador de cancelación** y **vista errores** diseñar vistas para ver el [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) y un [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociados con ellos.  
  
 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.  
  
|Opción de menú o pestaña|Descripción|  
|----------------------|-----------------|  
|**Ver [tipo de actividad]**|Seleccione esta opción de menú o pestaña para ver la representación gráfica predeterminada de la actividad seleccionada.|  
|**Ver controlador de cancelación**|Seleccione esta opción de menú o pestaña para ver el [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) asociado con la actividad seleccionada.|  
|**Ver controlador de errores**|Seleccione esta opción de menú o pestaña para ver el [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociado con la actividad seleccionada.|  
|**Ver controlador de compensación**|Seleccione esta opción de menú o pestaña para ver el [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) asociado seleccionado [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|  
|**Ver controlador de eventos**|Seleccione esta opción de menú o pestaña para ver el [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) asociado seleccionado el [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|  
  
 Para obtener información sobre vistas parecidas, vea [vistas de flujo de trabajo secuenciales (heredado)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## <a name="see-also"></a>Vea también  
 [Actividades de flujo de trabajo heredado](../workflow-designer/legacy-workflow-activities.md)   
 [Vistas de flujos de trabajo secuenciales (heredado)](../workflow-designer/sequential-workflow-views-legacy.md)