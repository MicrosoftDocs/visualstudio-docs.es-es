---
title: Diseñador de actividades FinalState | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dff9793becc3e0619d42b642609273f328c6aa73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656723"
---
# <a name="finalstate-activity-designer"></a>Diseñador de actividad FinalState
El diseñador de <xref:System.Activities.Core.Presentation.FinalState> se usa para crear un <xref:System.Activities.Statements.State> que finaliza una instancia de la máquina de estados.

## <a name="using-the-finalstate-activity-designer"></a>Usar el diseñador de actividad FinalState
 El diseñador de **FinalState** se usa para crear una <xref:System.Activities.Statements.State> que está preconfigurada como estado de terminación en una máquina de Estados. Un <xref:System.Activities.Statements.State> que se crea mediante el diseñador de actividades <xref:System.Activities.Core.Presentation.FinalState> tiene su propiedad <xref:System.Activities.Statements.State.IsFinal%2A> establecida en **true**, no tiene ninguna actividad <xref:System.Activities.Statements.State.Exit%2A> y ninguna transición procede de ella. Para utilizar el diseñador de actividades <xref:System.Activities.Core.Presentation.FinalState> para agregar una actividad <xref:System.Activities.Statements.State> que está preconfigurada como estado de terminación en una máquina de Estados, arrastre el diseñador de actividad **FinalState** desde la sección **máquina de Estados** del **cuadro de herramientas** y colóquelo en el diseñador de flujo de trabajo. El diseñador de actividad <xref:System.Activities.Core.Presentation.FinalState> se puede colocar sobre <xref:System.Activities.Statements.StateMachine> y agregar transiciones más adelante; o se puede crear una transición mientras se coloca el diseñador de actividad <xref:System.Activities.Core.Presentation.FinalState>. Para obtener más información sobre la creación de transiciones, vea [transición](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad State en el Diseñador de flujo de trabajo
 La tabla siguiente se muestran las propiedades que se pueden establecer mediante el diseñador de <xref:System.Activities.Core.Presentation.FinalState> y se describe cómo se usan en el diseñador. Algunas de estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.State> en el encabezado. El valor predeterminado es **State**. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades. <xref:System.Activities.Statements.State.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Statements.State.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica la acción que se produce cuando se entra en este estado. Este valor se puede establecer arrastrando una actividad desde el **cuadro de herramientas** y colocándolo en la sección <xref:System.Activities.Statements.State.Entry%2A> del estado.|

## <a name="see-also"></a>Vea también
 [Transición](../workflow-designer/transition-activity-designer.md) de [Estado](../workflow-designer/state-activity-designer.md) [StateMachine](../workflow-designer/statemachine-activity-designer.md)