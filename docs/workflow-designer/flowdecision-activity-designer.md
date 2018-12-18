---
title: Diseñador de flujo de trabajo - Diseñador de actividades FlowDecision
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a87c5c9ebe1b3eed2c3c569e508c5b76ce6845d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818996"
---
# <a name="flowdecision-activity-designer"></a>Diseñador de actividades FlowDecision

El nodo <xref:System.Activities.Statements.FlowDecision> es un nodo condicional que proporciona una bifurcación para el flujo de control en una alternativa entre dos, en función de si se ha satisfecho una condición especificada. Si el flujo requiere más de dos bifurcaciones, utilice <xref:System.Activities.Statements.FlowSwitch%601> en su lugar.

## <a name="the-flowdecision-node"></a>Nodo FlowDecision

Utilice el nodo <xref:System.Activities.Statements.FlowDecision> cuando se puedan crear bifurcaciones en dos direcciones a partir del flujo. Un nodo <xref:System.Activities.Statements.FlowDecision> tiene una propiedad <xref:System.Activities.Statements.FlowDecision.Condition%2A> y una clase <xref:System.Activities.Statements.FlowNode> asociadas a cada uno de los dos posibles resultados: <xref:System.Activities.Statements.FlowDecision.True%2A> o <xref:System.Activities.Statements.FlowDecision.False%2A>. Se evalúa <xref:System.Activities.Statements.FlowDecision.Condition%2A> y el valor resultante determina la clase <xref:System.Activities.Statements.FlowNode> siguiente que se va a procesar dentro de <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Utilizar el diseñador FlowDecision

El **FlowDecision** diseñador puede encontrarse en el **Flowchart** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **cuadro de herramientas** pestaña en el Diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** desde el **vista** menús o presione **Ctrl**+**Alt** + **X**.

El **FlowDecision** diseñador se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo dentro de un **Flowchart** Diseñador de actividad. Esto crea un <xref:System.Activities.Statements.FlowDecision> con la etiqueta **decisión** dentro de la <xref:System.Activities.Statements.Flowchart> actividad. El Diseñador de puntero del mouse y el **True** y **False** aparecen los identificadores cuadrados de las dos ramas.

Después de arrastrar el **FlowDecision** diseñador y otros diseñadores en el **Flowchart**, los nodos se pueden vincular entre sí para especificar el orden de ejecución. Para crear un vínculo entre un nodo de origen (incluido el **True** y **False** ramas de la **FlowDecision**) y un nodo de destino, el diseñador del nodo de origen del mouse y los identificadores cuadrados que aparecen en cada lado del mismo. Haga clic en uno de los identificadores cuadrados y arrástrelo manteniendo presionado el botón del mouse hasta uno de los identificadores que aparecen de forma similar en torno al nodo de destino cuando desplaza el mouse sobre el mismo. Suelte el botón del mouse y se creará un vínculo entre ambos nodos que quedará representado como una flecha desde el diseñador de origen hasta el diseñador de destino.

La expresión que indica que el <xref:System.Activities.Statements.FlowDecision.Condition%2A> pueden escribirse en el **condición** cuadro de la **propiedades** ventana haciendo clic donde aparece el texto de la sugerencia "Escriba una expresión de VB".

### <a name="the-flowdecision-properties"></a>Las propiedades FlowDecision

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.FlowDecision> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|La condición que determina la ruta de acceso que va a tomar el control de flujo.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|La ruta de acceso que toma el control de flujo si se satisface <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|La ruta de acceso que toma el control de flujo si no se satisface <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|

## <a name="see-also"></a>Vea también

- [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)
- [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T >](../workflow-designer/flowswitch-t-activity-designer.md)