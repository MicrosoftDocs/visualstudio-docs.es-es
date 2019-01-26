---
title: 'Diseñador de flujo de trabajo: si el Diseñador de actividad'
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f069da9bb84074544cc388ab2bf7fa1eab3c7595
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917164"
---
# <a name="if-activity-designer"></a>Diseñador de actividades If

La actividad <xref:System.Activities.Statements.If> evalúa una condición y ejecuta una actividad según los resultados de esa evaluación. Esta actividad es muy útil cuando se utiliza un estilo de modelado por procedimientos de programación. Una actividad <xref:System.Activities.Statements.If> puede estar anidada en una actividad <xref:System.Activities.Statements.Sequence> o en una actividad <xref:System.Activities.Statements.Parallel>, por ejemplo. Si está utilizando una actividad <xref:System.Activities.Statements.Flowchart>, plantéese utilizar una actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.

## <a name="if-properties-in-the-workflow-designer"></a>Propiedades If en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.If> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|La condición que determina qué actividad secundaria se va a ejecutar. Para establecer el <xref:System.Activities.Statements.If.Condition%2A>, escriba una expresión de Visual Basic en el **condición** cuadro en el **si** actividad diseñador o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.If.Else%2A>|False|La actividad que se ejecutarán si la <xref:System.Activities.Statements.If.Condition%2A> es **false**. Para agregar una actividad que es ejecutada por el <xref:System.Activities.Statements.If.Else%2A> bifurcar, coloque una actividad de la **cuadro de herramientas** en el **Else** cuadro en el **si** Diseñador de actividad con el texto de la sugerencia " Colocar actividad aquí".|
|<xref:System.Activities.Statements.If.Then%2A>|False|La actividad que se ejecutarán si la <xref:System.Activities.Statements.If.Condition%2A> es **true**. Para agregar una actividad que es ejecutada por el <xref:System.Activities.Statements.If.Then%2A> bifurcar, coloque una actividad de la **cuadro de herramientas** en el **, a continuación,** cuadro en el **si** Diseñador de actividad con el texto de la sugerencia " Colocar actividad aquí".|

## <a name="see-also"></a>Vea también

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)