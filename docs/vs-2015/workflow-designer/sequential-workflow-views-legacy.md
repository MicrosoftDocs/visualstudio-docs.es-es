---
title: Vistas de flujos de trabajo secuenciales (heredado) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 1ac9d10ddb687063de8c45296bc879854a0979a4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248734"
---
# <a name="sequential-workflow-views-legacy"></a>Vistas de flujos de trabajo secuenciales (Heredado)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] proporciona [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que se puede usar para tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 [!INCLUDE[wfd2](../includes/wfd2-md.md)] proporciona una manera de crear gráficamente aplicaciones de [!INCLUDE[wf](../includes/wf-md.md)] mediante la conocida interfaz de usuario de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[wf](../includes/wf-md.md)] las aplicaciones de flujo de trabajo están formadas por pasos de proceso de flujo de trabajo denominados actividades. Para crear un flujo de trabajo, cree actividades en la superficie de diseño arrastrando sus diseñadores de actividad correspondientes desde **cuadro de herramientas** a la superficie de diseño.  
  
 Cuando se crea un flujo de trabajo secuencial, que es un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), existen tres vistas del flujo de trabajo. Estas vistas son accesibles desde el **flujo de trabajo** menú y en el menú contextual en la superficie de diseño.  
  
 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.  
  
|Opción de menú o pestaña|Descripción|  
|----------------------|-----------------|  
|**Vista de flujo de trabajo secuencial**|Haga clic en la superficie de diseño y seleccione el **vista flujo de trabajo secuencial** opción en el menú contextual para mostrar el **flujo de trabajo secuencial** vista, que muestra la actividad basada gráfica representación del flujo de trabajo secuencial. O bien seleccione **vista flujo de trabajo secuencial** desde el **flujo de trabajo** menú.|  
|**Ver controlador de cancelación**|Haga clic en la superficie de diseño y seleccione el **ver controlador de cancelación** opción en el menú contextual para mostrar el **flujo de trabajo secuencial** ver, que muestra la [CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) actividad asociada con el flujo de trabajo. O bien seleccione **ver controlador de cancelación** desde el **flujo de trabajo** menú.|  
|**Ver controlador de errores**|Haga clic en la superficie de diseño y seleccione el **ver controlador de errores** opción en el menú contextual para mostrar el **errores** ver, que muestra la [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) actividad asociada con el flujo de trabajo. O bien seleccione **ver controlador de errores** desde el **flujo de trabajo** menú.|  
  
 Para obtener más información sobre vistas parecidas, vea [vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md).  
  
## <a name="see-also"></a>Vea también  
 [Vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md)   
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Modos de creación de flujo de trabajo](http://go.microsoft.com/fwlink?LinkID=65014)