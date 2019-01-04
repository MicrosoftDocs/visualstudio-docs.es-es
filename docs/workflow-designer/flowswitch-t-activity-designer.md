---
title: Diseñador de flujo de trabajo - FlowSwitch<T> Diseñador de actividad
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 046dd00b89b8f14da3082e60a04a92f8152ecc08
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942390"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T > Diseñador de actividad

La actividad <xref:System.Activities.Statements.FlowSwitch%601> es un nodo condicional que proporciona capacidad de bifurcación para el flujo de control según criterios de coincidencia cuando se necesitan más de dos bifurcaciones alternativas. Si la rama del flujo requiere dos rutas de acceso, utilice la actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.

## <a name="the-flowswitcht-activity"></a>La actividad FlowSwitch\<T > actividad

El <xref:System.Activities.Statements.FlowSwitch%601> actividad contiene una <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> que devuelve un valor de tipo *T* (especificado por el parámetro genérico) cuando se evalúa. La actividad también contiene un conjunto de propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, que especifica una asignación única de posibles resultados de esta evaluación para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>. El <xref:System.Activities.Statements.FlowNode> ejecutó tiene un objeto de tipo *T* coincide con el valor de evaluado <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Se puede proporcionar (opcionalmente) un caso <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> para el caso en el que no se obtuvo ninguna coincidencia.

### <a name="using-the-flowswitcht-activity-designer"></a>Uso de la actividad FlowSwitch\<T > Diseñador de actividad

El **FlowSwitch\<T >** Diseñador de actividad puede encontrarse en el **Flowchart** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **Cuadro de herramientas** ficha en el lado izquierdo del Diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** desde el **vista** menús o presione **Ctrl**+**Alt** + **X**.

El **FlowSwitch\<T >** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo dentro de un **Flowchart** Diseñador de actividad. Use el **seleccionar tipos** ventana que muestra para especificar el tipo (asociado en código con el <xref:System.Activities.Statements.FlowSwitch%601> por su parámetro genérico) obtenido de la evaluación de la <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Este procedimiento se crea un <xref:System.Activities.Statements.FlowSwitch%601> actividad etiquetada como **conmutador** dentro de la <xref:System.Activities.Statements.Flowchart> actividad. El <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> pueden escribirse en el **expresión** cuadro de la **propiedades** ventana haciendo clic donde aparece el texto de la sugerencia "Escriba una expresión de VB".

Mueva el mouse sobre el **FlowSwitch\<T >** Diseñador de actividades para hacer que los identificadores cuadrados que sirven para vincular <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> aparezca alrededor de los bordes. Después de arrastrar el **FlowSwitch < T\>**  Diseñador de actividad y otros diseñadores de actividad en el **Flowchart**, el <xref:System.Activities.Activity> objetos que representan están listos para vincularse entre sí para especificar el orden de ejecución. Para crear uno de los <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> asociado con el <xref:System.Activities.Statements.FlowSwitch%601>, haga clic en uno de los identificadores de caso de forma cuadrada en el perímetro de la **FlowSwitch < T\>**  y arrástrelo (manteniendo presionado el botón del mouse) hacia uno de los controladores que aparece de forma similar en torno a la actividad de destino cuando se mantiene el mouse sobre su diseñador. Suelte el botón del mouse y una flecha desde el **FlowSwitch < T\>**  hasta el Diseñador de destino, aparece que representa este caso. El valor predeterminado para este caso se muestra en la flecha y se puede editar en el **caso** cuadro de la **propiedades** ventana.

### <a name="the-flowswitcht-properties"></a>La actividad FlowSwitch\<T > Propiedades

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.FlowSwitch%601> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Especifica la expresión que se evalúa para determinar cuál de las propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> se va intercambiar en la ruta de acceso de ejecución.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Especifica una asignación única de los posibles resultados que se obtienen al evaluar la propiedad <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Especifica la asignación cuando la evaluación de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> no coincide con uno de los valores que contiene el objeto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Vea también

- [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)
- [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)