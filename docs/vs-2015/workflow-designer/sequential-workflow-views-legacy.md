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
ms.openlocfilehash: 8acc9bfcac476425ac6c6b967b1a3b3a34310d8a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663223"
---
# <a name="sequential-workflow-views-legacy"></a>Vistas de flujos de trabajo secuenciales (Heredado)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] proporciona [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que se puede usar para tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] proporciona una manera de crear gráficamente aplicaciones de [!INCLUDE[wf](../includes/wf-md.md)] mediante la conocida interfaz de usuario de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[wf](../includes/wf-md.md)] las aplicaciones de flujo de trabajo están formadas por pasos de proceso de flujo de trabajo denominados actividades. Para crear un flujo de trabajo, cree actividades en la superficie de diseño arrastrando sus diseñadores de actividad respectivos desde el **cuadro de herramientas** hasta la superficie de diseño.

 Cuando se crea un flujo de trabajo secuencial, que es un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), están disponibles tres vistas del flujo de trabajo. Estas vistas son accesibles desde el menú **flujo de trabajo** y desde el menú contextual en la superficie de diseño.

 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.

|Opción de menú o pestaña|Descripción|
|----------------------|-----------------|
|**Ver SequentialWorkflow**|Haga clic con el botón secundario en la superficie de diseño y seleccione la opción **Ver SequentialWorkflow** en el menú contextual para mostrar la vista **flujo de trabajo secuencial** , que muestra la representación gráfica basada en actividad del flujo de trabajo secuencial. O bien, seleccione **Ver SequentialWorkflow** en el menú **flujo de trabajo** .|
|**Ver controlador de cancelación**|Haga clic con el botón secundario en la superficie de diseño y seleccione la opción **Ver controlador de cancelación** en el menú contextual para mostrar la vista **flujo de trabajo secuencial** , que muestra la actividad [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) asociada al flujo de trabajo. O bien, seleccione **Ver controlador de cancelación** en el menú **flujo de trabajo** .|
|**Ver controlador de errores**|Haga clic con el botón secundario en la superficie de diseño y seleccione la opción **Ver controlador de errores** en el menú contextual para mostrar la vista **errores** , que muestra la actividad [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) asociada al flujo de trabajo. O bien, seleccione **Ver controlador de errores** en el menú **flujo de trabajo** .|

 Para obtener más información sobre vistas similares, consulte [vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Vea también
 [Vistas de actividad (heredado)](../workflow-designer/activity-views-legacy.md) [creación de proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md) [modos de creación de flujos](http://go.microsoft.com/fwlink?LinkID=65014) de trabajo