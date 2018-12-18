---
title: Diseñador de actividad de estado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: cc6d0d13b1bb924847c52ae8e41e2b859d2e7b2b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184020"
---
# <a name="state-activity-designer"></a>Diseñador de actividad State
<xref:System.Activities.Statements.State> representa un estado en el que una máquina de estados puede estar.  
  
## <a name="using-the-state-activity-designer"></a>Usar el diseñador de actividad State  
 Para agregar un <xref:System.Activities.Statements.State> a un flujo de trabajo, arrastre el **estado** Diseñador de actividades desde el **máquina de estados** sección de la **cuadro de herramientas** y colóquelo en una <xref:System.Activities.Statements.StateMachine> actividad en el [!INCLUDE[wfd1](../includes/wfd1-md.md)] superficie. Una actividad <xref:System.Activities.Statements.State> se puede colocar sobre <xref:System.Activities.Statements.StateMachine> y agregar transiciones más adelante; o se puede crear una transición mientras se coloca la actividad <xref:System.Activities.Statements.State>. Para agregar un <xref:System.Activities.Statements.State> actividad y crear una transición en un solo paso, arrastre un **estado** actividad desde la **máquina de estados** sección de la **cuadro de herramientas** y mantenga el mouse sobre otro estado en el Diseñador de flujo de trabajo. Cuando el <xref:System.Activities.Statements.State> arrastrado está sobre a otro <xref:System.Activities.Statements.State>, aparecerán cuatro triángulos alrededor del otro <xref:System.Activities.Statements.State>. Si <xref:System.Activities.Statements.State> se coloca sobre uno de los cuatro triángulos, se agrega a la máquina de estados y se crea una transición desde el <xref:System.Activities.Statements.State> de origen al <xref:System.Activities.Statements.State> de destino colocado. Para obtener más información, consulte [transición](../workflow-designer/transition-activity-designer.md).  
  
### <a name="state-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad State en el Diseñador de flujo de trabajo  
 La tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.State> que se pueden establecer mediante el diseñador de flujo de trabajo y se describe cómo se usan en el diseñador. Algunas de estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.State> en el encabezado. El valor predeterminado es **estado**. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades. <xref:System.Activities.Statements.State.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Statements.State.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica la acción que se produce cuando se entra en este estado. Cuando el <xref:System.Activities.Statements.State> actividad se expande, este valor se puede establecer arrastrando una actividad desde la **cuadro de herramientas** y colocándola sobre la **entrada** sección del estado.|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|Especifica la acción que se produce cuando se sale de este estado. Cuando el <xref:System.Activities.Statements.State> actividad se expande, este valor se puede establecer arrastrando una actividad desde la **cuadro de herramientas** y colocándola sobre la **Exit** sección del estado.|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Muestra las transiciones posibles que se originan desde <xref:System.Activities.Statements.State>. Cada elemento de la lista tiene un vínculo a la <xref:System.Activities.Statements.Transition> asociada y el <xref:System.Activities.Statements.State> de destino. Haciendo clic en el vínculo cambiará el diseñador a una vista expandida de <xref:System.Activities.Statements.Transition> o de <xref:System.Activities.Statements.State>.|  
  
## <a name="see-also"></a>Vea también  
 [Máquina de Estados](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)