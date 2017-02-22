---
title: "Vistas de flujos de trabajo secuenciales (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "vistas de flujos de trabajo secuenciales"
  - "flujos de trabajo secuenciales, vistas"
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vistas de flujos de trabajo secuenciales (Heredado)
[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] proporciona [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado que se puede usar para tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] proporciona una manera de crear gráficamente aplicaciones de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] mediante la conocida interfaz de usuario de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].Las aplicaciones de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] están formadas por pasos de proceso de flujo de trabajo denominados actividades.Para crear un flujo de trabajo, cree actividades en la superficie de diseño arrastrando sus diseñadores de actividad correspondientes desde el **Cuadro de herramientas** hasta la superficie de diseño.  
  
 Cuando se crea un flujo de trabajo secuencial, que es una clase [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), se dispone de tres vistas del flujo de trabajo.Se puede tener acceso a ellas desde el menú **Flujo de trabajo** y desde el menú contextual de la superficie de diseño.  
  
 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.  
  
|Opción de menú o pestaña|Descripción|  
|------------------------------|-----------------|  
|**Ver Flujo de trabajo secuencial**|Haga clic con el botón secundario en la superficie de diseño y seleccione la opción **Ver Flujo de trabajo secuencial** en el menú contextual para ver la vista **Flujo de trabajo secuencial**, que muestra la representación gráfica basada en actividad del flujo de trabajo secuencial.O bien, seleccione **Ver Flujo de trabajo secuencial** en el menú **Flujo de trabajo**.|  
|**Ver controlador de cancelación**|Haga clic con el botón secundario en la superficie de diseño y seleccione la opción **Ver controlador de cancelación** en el menú contextual para ver la vista **Flujo de trabajo secuencial**, que muestra la actividad de la clase [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) asociada con el flujo de trabajo.O bien, seleccione **Ver controlador de cancelación** en el menú **Flujo de trabajo**.|  
|**Ver controlador de errores**|Haga clic con el botón secundario en la superficie de diseño y seleccione la opción **Ver controlador de errores** en el menú contextual para ver la vista **Errores**, que muestra la actividad de la clase [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociada con el flujo de trabajo.También puede seleccionar **Ver controlador de errores** en el menú **Flujo de trabajo**.|  
  
 Para obtener más información sobre vistas parecidas, vea [Vistas de actividad \(Heredado\)](../workflow-designer/activity-views-legacy.md).  
  
## Vea también  
 [Vistas de actividad \(Heredado\)](../workflow-designer/activity-views-legacy.md)   
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Modos de creación de flujos de trabajo](http://go.microsoft.com/fwlink?LinkID=65014)