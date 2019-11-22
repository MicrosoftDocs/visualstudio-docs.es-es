---
title: Sequential Workflow Views (Legacy) | Microsoft Docs
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
ms.openlocfilehash: 859fa44b44a295dc3e9f27fc168092a9fe2beebf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292362"
---
# <a name="sequential-workflow-views-legacy"></a>Vistas de flujos de trabajo secuenciales (Heredado)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] proporciona [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que se puede usar para tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] proporciona una manera de crear gráficamente aplicaciones de [!INCLUDE[wf](../includes/wf-md.md)] mediante la conocida interfaz de usuario de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[wf](../includes/wf-md.md)] las aplicaciones de flujo de trabajo están formadas por pasos de proceso de flujo de trabajo denominados actividades. To create a workflow, compose activities on the design surface by dragging their respective activity designers from **Toolbox** onto the design surface.

 When you create a sequential workflow, which is a [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040), three views of the workflow are available. These views are accessible from the **Workflow** menu and from the context menu on the design surface.

 En la tabla siguiente se enumeran el nombre y la descripción de cada vista.

|Opción de menú o pestaña|Descripción|
|----------------------|-----------------|
|**View SequentialWorkflow**|Right-click the design surface and select the **View SequentialWorkflow** option from the context menu to display the **Sequential Workflow** view, which shows the activity-based graphical representation of the sequential workflow. Or select **View SequentialWorkflow** from the **Workflow** menu.|
|**View Cancel Handler**|Right-click the design surface and select the **View Cancel Handler** option from the context menu to display the **Sequential Workflow** view, which shows the [CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050) activity associated with the workflow. Or select **View Cancel Handler** from the **Workflow** menu.|
|**View Fault Handler**|Right-click the design surface and select the **View Fault Handler** option from the context menu to display the **Faults** view, which shows the [FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055) activity associated with the workflow. Or select **View Fault Handler** from the **Workflow** menu.|

 For more information about similar views, see [Activity Views (Legacy)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Vea también
 [Activity Views (Legacy)](../workflow-designer/activity-views-legacy.md) [Creating Legacy Workflow Projects](../workflow-designer/creating-legacy-workflow-projects.md) [Workflow Authoring Modes](https://go.microsoft.com/fwlink?LinkID=65014)