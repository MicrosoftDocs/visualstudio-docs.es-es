---
title: Diseñador de actividad FlowDecision | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7109b779cf33d226f44853e3f67c8609bd42fc1b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212893"
---
# <a name="flowdecision-activity-designer"></a>Diseñador de actividades FlowDecision
El nodo <xref:System.Activities.Statements.FlowDecision> es un nodo condicional que proporciona una bifurcación para el flujo de control en una alternativa entre dos, en función de si se ha satisfecho una condición especificada. Si el flujo requiere más de dos bifurcaciones, utilice <xref:System.Activities.Statements.FlowSwitch%601> en su lugar.  
  
## <a name="the-flowdecision-node"></a>Nodo FlowDecision  
 Utilice el nodo <xref:System.Activities.Statements.FlowDecision> cuando se puedan crear bifurcaciones en dos direcciones a partir del flujo. Un nodo <xref:System.Activities.Statements.FlowDecision> tiene una propiedad <xref:System.Activities.Statements.FlowDecision.Condition%2A> y una clase <xref:System.Activities.Statements.FlowNode> asociadas a cada uno de los dos posibles resultados: <xref:System.Activities.Statements.FlowDecision.True%2A> o <xref:System.Activities.Statements.FlowDecision.False%2A>. Se evalúa <xref:System.Activities.Statements.FlowDecision.Condition%2A> y el valor resultante determina la clase <xref:System.Activities.Statements.FlowNode> siguiente que se va a procesar dentro de <xref:System.Activities.Statements.Flowchart>.  
  
### <a name="using-the-flowdecision-designer"></a>Utilizar el diseñador FlowDecision  
 El **FlowDecision** diseñador puede encontrarse en el **Flowchart** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **cuadro de herramientas** pestaña en el [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **FlowDecision** diseñador se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] expuesta dentro de un **Flowchart** Diseñador de actividad. Esto crea un <xref:System.Activities.Statements.FlowDecision> con la etiqueta **decisión** dentro de la <xref:System.Activities.Statements.Flowchart> actividad. El Diseñador de puntero del mouse y el **True** y **False** aparecen los identificadores cuadrados de las dos ramas.  
  
 Después de arrastrar el **FlowDecision** diseñador y otros diseñadores en el **Flowchart**, los nodos se pueden vincular entre sí para especificar el orden de ejecución. Para crear un vínculo entre un nodo de origen (incluido el **True** y **False** ramas de la **FlowDecision**) y un nodo de destino, el diseñador del nodo de origen del mouse y los identificadores cuadrados que aparecen en cada lado del mismo. Haga clic en uno de los identificadores cuadrados y arrástrelo manteniendo presionado el botón del mouse hasta uno de los identificadores que aparecen de forma similar en torno al nodo de destino cuando desplaza el mouse sobre el mismo. Suelte el botón del mouse y se creará un vínculo entre ambos nodos que quedará representado como una flecha desde el diseñador de origen hasta el diseñador de destino.  
  
 La expresión que indica que el <xref:System.Activities.Statements.FlowDecision.Condition%2A> pueden escribirse en el **condición** cuadro de la **propiedades** ventana haciendo clic donde aparece el texto de la sugerencia "Escriba una expresión de VB".  
  
### <a name="the-flowdecision-properties"></a>Las propiedades FlowDecision  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.FlowDecision> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|La condición que determina la ruta de acceso que va a tomar el control de flujo.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|La ruta de acceso que toma el control de flujo si se satisface <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|La ruta de acceso que toma el control de flujo si no se satisface <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|  
  
## <a name="see-also"></a>Vea también  
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)   
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)