---
title: "Diseñador de actividades While | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: f232d8e6c4a1dab9000b8f0e0f3037d083acbbef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="while-activity-designer"></a>Diseñador de actividades While
El <xref:System.Activities.Statements.While> actividad ejecuta la actividad contenida en su <xref:System.Activities.Statements.While.Body%2A> mientras especificado <xref:System.Activities.Statements.While.Condition%2A> se evalúa como **true**. La actividad contenida nunca se puede ejecutar. Si desea ejecutar la actividad contenida al menos una vez, utilice la actividad <xref:System.Activities.Statements.DoWhile> en su lugar.  
  
## <a name="while-properties-in-workflow-designer"></a>Propiedades While en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.While> más útiles y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.While> en el encabezado. El valor predeterminado es While. El valor se puede editar en el **propiedades** ventana o directamente en el encabezado del Diseñador de actividad.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.While.Body%2A>|False|Contiene la actividad que se va a ejecutar mientras la <xref:System.Activities.Statements.While.Condition%2A> se evalúa como **true**.|  
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contiene la expresión de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] que se evalúa para determinar si se va a ejecutar la actividad en la propiedad <xref:System.Activities.Statements.While.Body%2A>.|  
  
## <a name="see-also"></a>Vea también  
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)