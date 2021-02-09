---
title: Diseñador de actividad Diseñador de flujo de trabajo-State
description: Obtenga información sobre la actividad StateMachine y cómo puede usar el diseñador de actividad State para agregar un estado a un flujo de trabajo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: abf4e81ecd258668c93b674410f029e6be0f5bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873520"
---
# <a name="state-activity-designer"></a>Diseñador de actividad State

<xref:System.Activities.Statements.State> representa un estado en el que una máquina de estados puede estar.

## <a name="using-the-state-activity-designer"></a>Usar el diseñador de actividad State

Para agregar un <xref:System.Activities.Statements.State> a un flujo de trabajo, arrastre el diseñador de actividad **State** desde la sección **máquina de Estados** del **cuadro de herramientas** y colóquelo en una <xref:System.Activities.Statements.StateMachine> actividad en la superficie de diseñador de flujo de trabajo. Una actividad <xref:System.Activities.Statements.State> se puede colocar sobre <xref:System.Activities.Statements.StateMachine> y agregar transiciones más adelante; o se puede crear una transición mientras se coloca la actividad <xref:System.Activities.Statements.State>. Para agregar una <xref:System.Activities.Statements.State> actividad y crear una transición en un paso, arrastre una actividad **State** desde la sección **máquina de Estados** del **cuadro de herramientas** y mantenga el mouse sobre otro estado en el diseñador de flujo de trabajo. Cuando el <xref:System.Activities.Statements.State> arrastrado está sobre a otro <xref:System.Activities.Statements.State>, aparecerán cuatro triángulos alrededor del otro <xref:System.Activities.Statements.State>. Si <xref:System.Activities.Statements.State> se coloca sobre uno de los cuatro triángulos, se agrega a la máquina de estados y se crea una transición desde el <xref:System.Activities.Statements.State> de origen al <xref:System.Activities.Statements.State> de destino colocado. Para obtener más información, vea [transición](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad State en el Diseñador de flujo de trabajo

La tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.State> que se pueden establecer mediante el diseñador de flujo de trabajo y se describe cómo se usan en el diseñador. Algunas de estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.State> en el encabezado. El valor predeterminado es **State**. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades. <xref:System.Activities.Statements.State.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Statements.State.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica la acción que se produce cuando se entra en este estado. Cuando <xref:System.Activities.Statements.State> se expande la actividad, este valor se puede establecer arrastrando una actividad desde el **cuadro de herramientas** y colocándolo en la sección **entrada** del estado.|
|<xref:System.Activities.Statements.State.Exit%2A>|False|Especifica la acción que se produce cuando se sale de este estado. Cuando <xref:System.Activities.Statements.State> se expande la actividad, este valor se puede establecer arrastrando una actividad desde el **cuadro de herramientas** y colocándolo en la sección de **salida** del estado.|
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Muestra las transiciones posibles que se originan desde <xref:System.Activities.Statements.State>. Cada elemento de la lista tiene un vínculo a la <xref:System.Activities.Statements.Transition> asociada y el <xref:System.Activities.Statements.State> de destino. Haciendo clic en el vínculo cambiará el diseñador a una vista expandida de <xref:System.Activities.Statements.Transition> o de <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Vea también

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transición](../workflow-designer/transition-activity-designer.md)
