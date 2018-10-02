---
title: Diseñador de actividad FinalState | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ecbbded923645a1b2bf6eafe9bbe038e0cb3b29c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577370"
---
# <a name="finalstate-activity-designer"></a>Diseñador de actividad FinalState
El diseñador de <xref:System.Activities.Core.Presentation.FinalState> se usa para crear un <xref:System.Activities.Statements.State> que finaliza una instancia de la máquina de estados.  
  
## <a name="using-the-finalstate-activity-designer"></a>Usar el diseñador de actividad FinalState  
 El **FinalState** diseñador se utiliza para crear un <xref:System.Activities.Statements.State> que está preconfigurado como estado de terminación en una máquina de Estados. Un <xref:System.Activities.Statements.State> que se crea utilizando el <xref:System.Activities.Core.Presentation.FinalState> Diseñador de actividad tiene su <xref:System.Activities.Statements.State.IsFinal%2A> propiedad establecida en **true**, no tiene ningún <xref:System.Activities.Statements.State.Exit%2A> actividad y ninguna transición procede de ella. Para usar el <xref:System.Activities.Core.Presentation.FinalState> Diseñador de actividad para agregar un <xref:System.Activities.Statements.State> actividad que está preconfigurado como estado de terminación en una máquina de Estados, arrastre el **FinalState** Diseñador de actividad de la **máquina de estados**sección de la **cuadro de herramientas** y colóquela en el Diseñador de flujo de trabajo. El diseñador de actividad <xref:System.Activities.Core.Presentation.FinalState> se puede colocar sobre <xref:System.Activities.Statements.StateMachine> y agregar transiciones más adelante; o se puede crear una transición mientras se coloca el diseñador de actividad <xref:System.Activities.Core.Presentation.FinalState>. Para obtener más información sobre cómo crear transiciones, consulte [transición](../workflow-designer/transition-activity-designer.md).  
  
### <a name="state-activity-properties-in-the-workflow-designer"></a>Propiedades de la actividad State en el Diseñador de flujo de trabajo  
 La tabla siguiente se muestran las propiedades que se pueden establecer mediante el diseñador de <xref:System.Activities.Core.Presentation.FinalState> y se describe cómo se usan en el diseñador. Algunas de estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.State> en el encabezado. El valor predeterminado es **estado**. El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades. <xref:System.Activities.Statements.State.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Statements.State.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica la acción que se produce cuando se entra en este estado. Este valor se puede establecer arrastrando una actividad desde la **cuadro de herramientas** y colocándola sobre la <xref:System.Activities.Statements.State.Entry%2A> sección del estado.|  
  
## <a name="see-also"></a>Vea también  
 [Máquina de Estados](../workflow-designer/statemachine-activity-designer.md)   
 [Estado](../workflow-designer/state-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)