---
title: "Diseñador de actividad de secuencia | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 51f138d17c2b0f8d8a483ef09c298d1dbbf9345c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="sequence-activity-designer"></a>Diseñador actividades Sequence
La actividad <xref:System.Activities.Statements.Sequence> contiene una colección ordenada de actividades secundarias que ejecuta por orden.  
  
 Otra manera de ejecutar un conjunto de actividades por orden es utilizar una actividad <xref:System.Activities.Statements.Flowchart>. Considere el uso de la [Flowchart](../workflow-designer/flowchart-activity-designer.md) cuando haya una bifurcación simple o un bucle flujo del programa que desee en el diagrama del modelo.  
  
## <a name="using-the-sequence-activity-designer"></a>Utilizar el diseñador de actividades Sequence  
 Para agregar un <xref:System.Activities.Statements.Sequence> actividad, arrastre el **secuencia** Diseñador de actividad desde la **cuadro de herramientas** y colóquelo en el [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] superficie. Para agregar una actividad secundaria a esta <xref:System.Activities.Statements.Sequence> actividad, arrastre alguna otra actividad desde la **cuadro de herramientas** y colóquelo en el triángulo en el cuadro con el texto de la sugerencia "Coloque la actividad aquí".  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad Sequence en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Sequence> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.Sequence> en el encabezado. El valor predeterminado es Sequence. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
  
## <a name="see-also"></a>Vea también  
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)