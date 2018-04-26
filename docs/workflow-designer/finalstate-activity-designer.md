---
title: Diseñador de flujo de trabajo - Diseñador de actividad FinalState
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d89e9f81bb7dc8237069a79784eadc0e5d375d6e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="finalstate-activity-designer"></a>Diseñador de actividad FinalState

El diseñador de <xref:System.Activities.Core.Presentation.FinalState> se usa para crear un <xref:System.Activities.Statements.State> que finaliza una instancia de la máquina de estados.

## <a name="using-the-finalstate-activity-designer"></a>Usar el diseñador de actividad FinalState

El **FinalState** diseñador se utiliza para crear un <xref:System.Activities.Statements.State> que está preconfigurado como estado de terminación en una máquina de Estados. A <xref:System.Activities.Statements.State> que se creó mediante la <xref:System.Activities.Core.Presentation.FinalState> Diseñador de actividad tiene su <xref:System.Activities.Statements.State.IsFinal%2A> propiedad establecida en **true**, no tiene ningún <xref:System.Activities.Statements.State.Exit%2A> actividad y ninguna transición procede de ella. Para usar el <xref:System.Activities.Core.Presentation.FinalState> Diseñador de actividad para agregar una <xref:System.Activities.Statements.State> actividad que está preconfigurada como estado de terminación en una máquina de Estados, arrastre el **FinalState** Diseñador de actividad del **máquina de estados**sección de la **cuadro de herramientas** y se coloca en el Diseñador de flujo de trabajo. El diseñador de actividad <xref:System.Activities.Core.Presentation.FinalState> se puede colocar sobre <xref:System.Activities.Statements.StateMachine> y agregar transiciones más adelante; o se puede crear una transición mientras se coloca el diseñador de actividad <xref:System.Activities.Core.Presentation.FinalState>. Para obtener más información sobre la creación de transiciones, consulte [transición](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad State en el Diseñador de flujo de trabajo

La tabla siguiente se muestran las propiedades que se pueden establecer mediante el diseñador de <xref:System.Activities.Core.Presentation.FinalState> y se describe cómo se usan en el diseñador. Algunas de estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.State> en el encabezado. El valor predeterminado es **estado**. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades. <xref:System.Activities.Statements.State.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Statements.State.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica la acción que se produce cuando se entra en este estado. Este valor se puede establecer arrastrando una actividad desde la **cuadro de herramientas** y colocándola sobre la <xref:System.Activities.Statements.State.Entry%2A> sección del estado.|

## <a name="see-also"></a>Vea también

- [Máquina de Estados](../workflow-designer/statemachine-activity-designer.md)
- [Estado](../workflow-designer/state-activity-designer.md)
- [transición](../workflow-designer/transition-activity-designer.md)