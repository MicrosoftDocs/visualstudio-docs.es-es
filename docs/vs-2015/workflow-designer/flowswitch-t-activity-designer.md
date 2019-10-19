---
title: Diseñador de actividad de FlowSwitch &lt;T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27abb660766a7c04742eca221432af19f05f0d28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656645"
---
# <a name="flowswitchlttgt-activity-designer"></a>Diseñador de actividad de FlowSwitch &lt;T &gt;
La actividad <xref:System.Activities.Statements.FlowSwitch%601> es un nodo condicional que proporciona capacidad de bifurcación para el flujo de control según criterios de coincidencia cuando se necesitan más de dos bifurcaciones alternativas. Si la bifurcación del flujo requiere dos rutas de acceso, utilice la actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.

## <a name="the-flowswitcht-activity"></a>Actividad de > de \<T de FlowSwitch
 La actividad <xref:System.Activities.Statements.FlowSwitch%601> contiene una <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> que devuelve un valor de tipo *t* (especificado por el parámetro genérico) cuando se evalúa. La actividad también contiene un conjunto de propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, que especifica una asignación única de posibles resultados de esta evaluación para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>. La <xref:System.Activities.Statements.FlowNode> ejecutada es aquella cuyo objeto de tipo *t* coincide con el valor de la <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> evaluada. Se puede proporcionar (opcionalmente) un caso <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> para el caso en el que no se obtuvo ninguna coincidencia.

### <a name="using-the-flowswitcht-activity-designer"></a>Usar el diseñador de actividades FlowSwitch \<T >
 El diseñador de actividades **FlowSwitch \<T >** se puede encontrar en la categoría **Diagrama de flujo** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** en el lado izquierdo de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **FlowSwitch \<T >** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)] dentro de un diseñador de actividades **Flowchart** . Use la ventana **seleccionar tipos** que se muestra para especificar el tipo (asociado en el código con el <xref:System.Activities.Statements.FlowSwitch%601> por su parámetro genérico) obtenido al evaluar la <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Este procedimiento crea una actividad <xref:System.Activities.Statements.FlowSwitch%601> etiqueta **Switch** en la actividad <xref:System.Activities.Statements.Flowchart>. El <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> se puede escribir en el cuadro **expresión** de la ventana **propiedades** ; para ello, haga clic en el texto de la sugerencia "Escriba una expresión de VB".

 Pasar el puntero del mouse sobre el diseñador de actividad **FlowSwitch \<T >** para que los identificadores cuadrados que se usan para vincular <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> aparezcan alrededor de los bordes. Después de arrastrar el diseñador de actividad **FlowSwitch < T \>** y otros diseñadores de actividad al **Diagrama de flujo**, los objetos <xref:System.Activities.Activity> que representan están listos para que se vinculen entre sí para especificar el orden de ejecución. Para crear uno de los <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> asociados con el <xref:System.Activities.Statements.FlowSwitch%601>, haga clic en uno de los manipuladores de mayúsculas y minúsculas en el perímetro del **\<T de FlowSwitch >** y arrástrelo (manteniendo presionado el botón del mouse) a uno de los controladores que aparecen de forma similar en torno al actividad de destino cuando se mantiene el mouse sobre su diseñador. Suelte el botón del mouse y una flecha desde el **\<T FlowSwitch >** al diseñador de destino que representa este caso. El valor predeterminado de este caso se muestra en la flecha y se puede editar en el cuadro **caso** de la ventana **propiedades** .

### <a name="the-flowswitcht-properties"></a>Propiedades de > del \<T FlowSwitch
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.FlowSwitch%601> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Especifica la expresión que se evalúa para determinar cuál de las propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> se va intercambiar en la ruta de acceso de ejecución.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Especifica una asignación única de los posibles resultados que se obtienen al evaluar la propiedad <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Especifica la asignación cuando la evaluación de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> no coincide con uno de los valores que contiene el objeto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Vea también
 [Diagrama de](../workflow-designer/flowchart-activity-designers.md) [flujo](../workflow-designer/flowchart-activity-designer.md) Flowchart [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)