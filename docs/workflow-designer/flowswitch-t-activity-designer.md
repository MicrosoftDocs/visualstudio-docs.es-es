---
title: Diseñador de flujo de trabajo el &lt; Diseñador de &gt; actividades FlowSwitch T
description: Obtenga información sobre cómo la <T> actividad FlowSwitch es un nodo condicional que proporciona bifurcación para el flujo de control basado en los criterios de coincidencia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4eff69f1da5d2bc8c5f397b0cc6d21492a0a8d20
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435800"
---
# <a name="flowswitcht-activity-designer"></a>Diseñador de actividad FlowSwitch\<T>

La actividad <xref:System.Activities.Statements.FlowSwitch%601> es un nodo condicional que proporciona capacidad de bifurcación para el flujo de control según criterios de coincidencia cuando se necesitan más de dos bifurcaciones alternativas. Si la bifurcación del flujo requiere dos rutas de acceso, utilice la actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.

## <a name="the-flowswitcht-activity"></a>La \<T> actividad FlowSwitch

La <xref:System.Activities.Statements.FlowSwitch%601> actividad contiene un <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> que devuelve un valor de tipo *T* (especificado por el parámetro genérico) cuando se evalúa. La actividad también contiene un conjunto de propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, que especifica una asignación única de posibles resultados de esta evaluación para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>. La <xref:System.Activities.Statements.FlowNode> ejecutada es aquella cuyo objeto de tipo *T* coincide con el valor del evaluado <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Se puede proporcionar (opcionalmente) un caso <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> para el caso en el que no se obtuvo ninguna coincidencia.

### <a name="using-the-flowswitcht-activity-designer"></a>Usar el \<T> Diseñador de actividades FlowSwitch

El diseñador de actividades **FlowSwitch \<T>** se puede encontrar en la categoría **Diagrama de flujo** del cuadro de **herramientas** , al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** en el lado izquierdo del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

El diseñador de actividades **FlowSwitch \<T>** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo dentro de un diseñador de actividades **Flowchart** . Use la ventana **seleccionar tipos** que se muestra para especificar el tipo (asociado en el código con <xref:System.Activities.Statements.FlowSwitch%601> por su parámetro genérico) obtenido al evaluar <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Este procedimiento crea una <xref:System.Activities.Statements.FlowSwitch%601> actividad con etiqueta **Switch** dentro de la <xref:System.Activities.Statements.Flowchart> actividad. <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>Se puede escribir en el cuadro **expresión** de la ventana **propiedades** si se hace clic en donde aparece el texto de la sugerencia "Escriba una expresión de VB".

Pasar el mouse sobre el diseñador de actividad **FlowSwitch \<T>** para que los identificadores cuadrados que se usan para vincular <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> aparezcan alrededor de los bordes. Después de arrastrar el diseñador de actividades **FlowSwitch<T \>** y otros diseñadores de actividad al **Diagrama de flujo** , los <xref:System.Activities.Activity> objetos que representan están listos para que se vinculen entre sí para especificar el orden de ejecución. Para crear uno de los <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> asociados con el <xref:System.Activities.Statements.FlowSwitch%601> , haga clic en uno de los manipuladores de mayúsculas y minúsculas en el perímetro del **FlowSwitch<T \>** y arrástrelo (manteniendo presionado el botón del mouse) en uno de los identificadores que aparecen de forma similar en torno a la actividad de destino cuando el mouse se mantiene sobre su diseñador. Suelte el botón del mouse y una flecha desde **FlowSwitch<T \>** hasta el diseñador de destino que representa este caso. El valor predeterminado de este caso se muestra en la flecha y se puede editar en el cuadro **caso** de la ventana **propiedades** .

### <a name="the-flowswitcht-properties"></a>Propiedades de FlowSwitch \<T>

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.FlowSwitch%601> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Especifica la expresión que se evalúa para determinar cuál de las propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> se va intercambiar en la ruta de acceso de ejecución.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Falso|Especifica una asignación única de los posibles resultados que se obtienen al evaluar la propiedad <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Especifica la asignación cuando la evaluación de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> no coincide con uno de los valores que contiene el objeto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Consulte también

- [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)
- [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
