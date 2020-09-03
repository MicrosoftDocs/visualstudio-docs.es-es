---
title: Diseñador de actividad if | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6b35fe7f1b55dde25ec896f230f66cef00d24eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659055"
---
# <a name="if-activity-designer"></a>Diseñador de actividades If
La actividad <xref:System.Activities.Statements.If> evalúa una condición y ejecuta una actividad según los resultados de esa evaluación. Esta actividad es muy útil cuando se utiliza un estilo de modelado por procedimientos de programación. Una actividad <xref:System.Activities.Statements.If> puede estar anidada en una actividad <xref:System.Activities.Statements.Sequence> o en una actividad <xref:System.Activities.Statements.Parallel>, por ejemplo. Si está utilizando una actividad <xref:System.Activities.Statements.Flowchart>, plantéese utilizar una actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.

## <a name="if-properties-in-the-workflow-designer"></a>Propiedades If en el Diseñador de flujo de trabajo
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.If> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.If.Condition%2A>|Verdadero|La condición que determina qué actividad secundaria se va a ejecutar. Para establecer <xref:System.Activities.Statements.If.Condition%2A> , escriba una [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expresión en el cuadro **condición** en el diseñador de actividades **If** o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.If.Else%2A>|Falso|Actividad que se va a ejecutar si <xref:System.Activities.Statements.If.Condition%2A> es **false**. Para agregar una actividad que ejecute la <xref:System.Activities.Statements.If.Else%2A> bifurcación, coloque una actividad del cuadro de **herramientas** en el cuadro **else** del diseñador de actividad **If** con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.If.Then%2A>|Falso|Actividad que se va a ejecutar si <xref:System.Activities.Statements.If.Condition%2A> es **true**. Para agregar una actividad que ejecute la <xref:System.Activities.Statements.If.Then%2A> bifurcación, coloque una actividad del cuadro de **herramientas** en el cuadro **then** del diseñador de actividad **If** con el texto de la sugerencia "Coloque la actividad aquí".|

## <a name="see-also"></a>Consulte también
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md) [paralelo](../workflow-designer/parallel-activity-designer.md) de [secuencia](../workflow-designer/sequence-activity-designer.md)