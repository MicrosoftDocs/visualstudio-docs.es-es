---
title: "Vistas de actividad (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "actividades, vistas de actividad"
  - "vistas de actividad"
  - "vistas, actividad"
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vistas de actividad (Heredado)
Muchas de las actividades proporcionadas por [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], a partir de las que se crean flujos de trabajo, disponen de varias vistas de diseño en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado.Al arrastrar un diseñador de actividad del **Cuadro de herramientas** a la superficie de diseño, y siempre que vuelva a seleccionar la actividad posteriormente, puede pasar de una vista de diseño a otra mediante el menú **Flujo de trabajo** o haciendo clic con el botón secundario en la actividad seleccionada.Además, si mueve el puntero sobre el nombre de una actividad seleccionada, aparece un conjunto desplegable de pestañas, que puede utilizar para pasar de una vista a otra.  
  
 Cada actividad tiene por lo menos una vista, que es la vista predeterminada que se muestra al arrastrar un diseñador de actividad del **Cuadro de herramientas** a la superficie de diseño.Esta vista predeterminada de la actividad está disponible como opción **Ver \[tipo de actividad\]** en los menús y la pestaña, por ejemplo, **Ver Parallel**.La mayoría de las actividades tienen vistas adicionales y distintas actividades pueden tener vistas diferentes.Por ejemplo, la actividad [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) tiene la vista de compensación y la actividad [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) tiene una vista de eventos.Muchas de las actividades predefinidas de Windows Workflow Foundation tienen las vistas de diseño **Ver controlador de cancelación** y **Ver controlador de errores** para ver la actividad [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) y una actividad [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociada.  
  
 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.  
  
|Opción de menú o pestaña|Descripción|  
|------------------------------|-----------------|  
|**Ver \[tipo de actividad\]**|Seleccione esta opción de menú o pestaña para ver la representación gráfica predeterminada de la actividad seleccionada.|  
|**Ver controlador de cancelación**|Seleccione esta opción de menú o pestaña para ver la actividad [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) asociada a la actividad seleccionada.|  
|**Ver controlador de errores**|Seleccione esta opción de menú o pestaña para ver la actividad [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociada a la actividad seleccionada.|  
|**Ver controlador de compensación**|Seleccione esta opción de menú o pestaña para ver la actividad [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) asociada a la actividad [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) seleccionada.|  
|**Ver controlador de eventos**|Seleccione esta opción de menú o pestaña para ver la actividad [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) asociada a la actividad [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) seleccionada.|  
  
 Para obtener información sobre vistas parecidas, vea [Vistas de flujos de trabajo secuenciales \(Heredado\)](../workflow-designer/sequential-workflow-views-legacy.md).  
  
## Vea también  
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)   
 [Vistas de flujos de trabajo secuenciales \(Heredado\)](../workflow-designer/sequential-workflow-views-legacy.md)