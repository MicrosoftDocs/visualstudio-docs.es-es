---
title: "Diseñador de actividades TerminateWorkflow | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: e114f95baf771d8138fd155cf79f6e0ddbf14485
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="terminateworkflow-activity-designer"></a>Diseñador actividades TerminateWorkflow
El **TerminateWorkflow** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.TerminateWorkflow> actividad.  
  
## <a name="the-terminateworkflow-activity"></a>Actividad TerminateWorkflow  
 La actividad <xref:System.Activities.Statements.TerminateWorkflow> finaliza la ejecución de un flujo de trabajo.  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>Utilizar el diseñador de actividades TerminateWorkflow  
 El **TerminateWorkflow** Diseñador de actividad puede encontrarse en el **en tiempo de ejecución** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas** pestaña (o bien, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **TerminateWorkflow** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Esto crea una <xref:System.Activities.Statements.TerminateWorkflow> actividad con el valor predeterminado es **DisplayName** de TerminateWorkflow. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **TerminateWorkflow** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-terminateworkflow-properties"></a>Propiedades TerminateWorkflow  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TerminateWorkflow> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.TerminateWorkflow>. El valor predeterminado es TerminateWorkflow. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|La excepción que se va a producir cuando se finaliza el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|La razón que explica por qué finalizó el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|  
  
## <a name="see-also"></a>Vea también  
 [En tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)   
 [Conservar](../workflow-designer/persist-activity-designer.md)