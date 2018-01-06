---
title: "FlowSwitch&lt;T&gt; Diseñador de actividad | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: c3e757d8ffea7e91c2d5e51bc4a04e6225d1064f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt; Diseñador de actividad
La actividad <xref:System.Activities.Statements.FlowSwitch%601> es un nodo condicional que proporciona capacidad de bifurcación para el flujo de control según criterios de coincidencia cuando se necesitan más de dos bifurcaciones alternativas. Si la bifurcación del flujo requiere dos rutas de acceso, utilice la actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.  
  
## <a name="the-flowswitcht-activity"></a>El FlowSwitch < T\> actividad  
 El <xref:System.Activities.Statements.FlowSwitch%601> actividad contiene un <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> que devuelve un valor de tipo *T* (especificada por el parámetro genérico) cuando se evalúa. La actividad también contiene un conjunto de propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, que especifica una asignación única de posibles resultados de esta evaluación para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>. El <xref:System.Activities.Statements.FlowNode> ejecuta es el objeto de tipo *T* coincide con el valor de evaluado <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Se puede proporcionar (opcionalmente) un caso <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> para el caso en el que no se obtuvo ninguna coincidencia.  
  
### <a name="using-the-flowswitcht-activity-designer"></a>Mediante el FlowSwitch\<T > Diseñador de actividad  
 El **FlowSwitch\<T >** Diseñador de actividad puede encontrarse en el **Flowchart** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **Cuadro de herramientas** ficha en el lado izquierdo de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **FlowSwitch\<T >** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta dentro de un **diagrama de flujo** Diseñador de actividad. Use la **seleccionar tipos de** ventana que se muestra para especificar el tipo (asociado en código con la <xref:System.Activities.Statements.FlowSwitch%601> por su parámetro genérico) obtuvo al evaluar la <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Este procedimiento crea una <xref:System.Activities.Statements.FlowSwitch%601> actividad etiquetada como **conmutador** dentro de la <xref:System.Activities.Statements.Flowchart> actividad. El <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> pueden escribirse en el **expresión** cuadro de la **propiedades** ventana haciendo clic donde aparece el texto de la sugerencia "Escriba una expresión de VB".  
  
 Mueva el mouse sobre la **FlowSwitch\<T >** Diseñador de actividades para hacer que los identificadores cuadrados que sirven para vincular la <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> que aparezcan alrededor de los bordes. Después de arrastrar el **FlowSwitch < T\>**  Diseñador de actividades y otros diseñadores de actividad en el **Flowchart**, el <xref:System.Activities.Activity> objetos que representan están listos para vincularse entre sí para especificar el orden de ejecución. Para crear uno de los <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> asociados con el <xref:System.Activities.Statements.FlowSwitch%601>, haga clic en uno de los identificadores cuadrados mayúsculas en el perímetro de la **FlowSwitch < T\>**  y arrástrelo (manteniendo presionado el botón del mouse) a uno de los controladores que aparece en forma similar rodeando la actividad de destino cuando se desplaza el mouse sobre su diseñador. Suelte el botón del mouse y una flecha desde el **FlowSwitch < T\>**  para el Diseñador de destino no parece que representa este caso. El valor predeterminado para este caso se muestra en la flecha y pueden modificarse en el **caso** cuadro de la **propiedades** ventana.  
  
### <a name="the-flowswitcht-properties"></a>El FlowSwitch < T\> propiedades  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.FlowSwitch%601> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Especifica la expresión que se evalúa para determinar cuál de las propiedades <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> se va intercambiar en la ruta de acceso de ejecución.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Especifica una asignación única de los posibles resultados que se obtienen al evaluar la propiedad <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> para un conjunto de objetos <xref:System.Activities.Statements.FlowNode>.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Especifica la asignación cuando la evaluación de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> no coincide con uno de los valores que contiene el objeto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|  
  
## <a name="see-also"></a>Vea también  
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)   
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)