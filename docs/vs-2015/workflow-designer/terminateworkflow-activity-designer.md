---
title: Diseñador actividades TerminateWorkflow | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: a00677390967f0cc0cff8a04b33895d7c88588f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578486"
---
# <a name="terminateworkflow-activity-designer"></a>Diseñador actividades TerminateWorkflow
El **TerminateWorkflow** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.TerminateWorkflow> actividad.  
  
## <a name="the-terminateworkflow-activity"></a>Actividad TerminateWorkflow  
 La actividad <xref:System.Activities.Statements.TerminateWorkflow> finaliza la ejecución de un flujo de trabajo.  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>Utilizar el diseñador de actividades TerminateWorkflow  
 El **TerminateWorkflow** Diseñador de actividad puede encontrarse en el **en tiempo de ejecución** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas** ficha (como alternativa, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **TerminateWorkflow** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.TerminateWorkflow> actividad con un valor predeterminado **DisplayName** de TerminateWorkflow. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **TerminateWorkflow** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.  
  
### <a name="the-terminateworkflow-properties"></a>Propiedades TerminateWorkflow  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TerminateWorkflow> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.TerminateWorkflow>. El valor predeterminado es TerminateWorkflow. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|La excepción que se va a producir cuando se finaliza el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|La razón que explica por qué finalizó el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|  
  
## <a name="see-also"></a>Vea también  
 [En tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)