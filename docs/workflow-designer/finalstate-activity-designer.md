---
title: Diseñador de actividades Diseñador de flujo de trabajo-FinalState
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23e8973de1deba610a90e21edb870000abbb03e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875597"
---
# <a name="finalstate-activity-designer"></a>Diseñador de actividad FinalState

El diseñador de <xref:System.Activities.Core.Presentation.FinalState> se usa para crear un <xref:System.Activities.Statements.State> que finaliza una instancia de la máquina de estados.

## <a name="using-the-finalstate-activity-designer"></a>Usar el diseñador de actividad FinalState

El diseñador de **FinalState** se usa para crear un <xref:System.Activities.Statements.State> que está preconfigurado como un estado de terminación en una máquina de Estados. Un <xref:System.Activities.Statements.State> que se crea mediante el <xref:System.Activities.Core.Presentation.FinalState> Diseñador de actividad tiene su <xref:System.Activities.Statements.State.IsFinal%2A> propiedad establecida en **true**, no tiene ninguna <xref:System.Activities.Statements.State.Exit%2A> actividad y ninguna transición procede de ella. Para usar el <xref:System.Activities.Core.Presentation.FinalState> Diseñador de actividad para agregar una <xref:System.Activities.Statements.State> actividad que está preconfigurada como estado de terminación en una máquina de Estados, arrastre el diseñador de actividad **FinalState** desde la sección **máquina de Estados** del cuadro de **herramientas** y colóquelo en el diseñador de flujo de trabajo. El diseñador de actividad <xref:System.Activities.Core.Presentation.FinalState> se puede colocar sobre <xref:System.Activities.Statements.StateMachine> y agregar transiciones más adelante; o se puede crear una transición mientras se coloca el diseñador de actividad <xref:System.Activities.Core.Presentation.FinalState>. Para obtener más información sobre la creación de transiciones, vea [transición](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad State en el Diseñador de flujo de trabajo

La tabla siguiente se muestran las propiedades que se pueden establecer mediante el diseñador de <xref:System.Activities.Core.Presentation.FinalState> y se describe cómo se usan en el diseñador. Algunas de estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Falso|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.State> en el encabezado. El valor predeterminado es **State**. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades. <xref:System.Activities.Statements.State.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Statements.State.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.State.Entry%2A>|Falso|Especifica la acción que se produce cuando se entra en este estado. Este valor se puede establecer arrastrando una actividad del cuadro de **herramientas** y colocándolo en la <xref:System.Activities.Statements.State.Entry%2A> sección del estado.|

## <a name="see-also"></a>Consulte también

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
- [Transición](../workflow-designer/transition-activity-designer.md)