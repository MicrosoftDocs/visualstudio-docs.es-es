---
title: Diseñador de actividades Diseñador de flujo de trabajo-if
description: Obtenga información sobre cómo la actividad if evalúa una condición y ejecuta una actividad según los resultados de esa evaluación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2daa2ab6e3f41d5447204db573b8ae228d617fdf
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437819"
---
# <a name="if-activity-designer"></a>Diseñador de actividades If

La actividad <xref:System.Activities.Statements.If> evalúa una condición y ejecuta una actividad según los resultados de esa evaluación. Esta actividad es muy útil cuando se utiliza un estilo de modelado por procedimientos de programación. Una actividad <xref:System.Activities.Statements.If> puede estar anidada en una actividad <xref:System.Activities.Statements.Sequence> o en una actividad <xref:System.Activities.Statements.Parallel>, por ejemplo. Si está utilizando una actividad <xref:System.Activities.Statements.Flowchart>, plantéese utilizar una actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.

## <a name="if-properties-in-the-workflow-designer"></a>Propiedades If en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.If> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|La condición que determina qué actividad secundaria se va a ejecutar. Para establecer <xref:System.Activities.Statements.If.Condition%2A> , escriba una expresión de Visual Basic en el cuadro **condición** en el diseñador de actividades **If** o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.If.Else%2A>|Falso|Actividad que se va a ejecutar si <xref:System.Activities.Statements.If.Condition%2A> es **false**. Para agregar una actividad que ejecute la <xref:System.Activities.Statements.If.Else%2A> bifurcación, coloque una actividad del cuadro de **herramientas** en el cuadro **else** del diseñador de actividad **If** con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.If.Then%2A>|Falso|Actividad que se va a ejecutar si <xref:System.Activities.Statements.If.Condition%2A> es **true**. Para agregar una actividad que ejecute la <xref:System.Activities.Statements.If.Then%2A> bifurcación, coloque una actividad del cuadro de **herramientas** en el cuadro **then** del diseñador de actividad **If** con el texto de la sugerencia "Coloque la actividad aquí".|

## <a name="see-also"></a>Consulte también

- [Secuencia](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
