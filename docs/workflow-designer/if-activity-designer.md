---
title: "Si el Diseñador de actividad | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 950bff10372c9c40e047f891049e7cc387c8efc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="if-activity-designer"></a>Diseñador de actividades If
La actividad <xref:System.Activities.Statements.If> evalúa una condición y ejecuta una actividad según los resultados de esa evaluación. Esta actividad es muy útil cuando se utiliza un estilo de modelado por procedimientos de programación. Una actividad <xref:System.Activities.Statements.If> puede estar anidada en una actividad <xref:System.Activities.Statements.Sequence> o en una actividad <xref:System.Activities.Statements.Parallel>, por ejemplo. Si está utilizando una actividad <xref:System.Activities.Statements.Flowchart>, plantéese utilizar una actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.  
  
## <a name="if-properties-in-the-workflow-designer"></a>Propiedades If en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.If> más útiles y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|La condición que determina qué actividad secundaria se va a ejecutar. Para establecer el <xref:System.Activities.Statements.If.Condition%2A>, escriba un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] expresión en el **condición** cuadro en el **si** actividad diseñador o en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|La actividad que se va a ejecutar si el <xref:System.Activities.Statements.If.Condition%2A> es **false**. Para agregar una actividad que se ejecuta mediante el <xref:System.Activities.Statements.If.Else%2A> crear una bifurcación, coloque una actividad de la **cuadro de herramientas** en el **Else** cuadro en el **si** Diseñador de actividad con el texto de la sugerencia " Coloque la actividad aquí".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|La actividad que se va a ejecutar si el <xref:System.Activities.Statements.If.Condition%2A> es **true**. Para agregar una actividad que se ejecuta mediante el <xref:System.Activities.Statements.If.Then%2A> crear una bifurcación, coloque una actividad de la **cuadro de herramientas** en el **, a continuación,** cuadro en el **si** Diseñador de actividad con el texto de la sugerencia " Coloque la actividad aquí".|  
  
## <a name="see-also"></a>Vea también  
 [Secuencia](../workflow-designer/sequence-activity-designer.md)   
 [Paralelo](../workflow-designer/parallel-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)