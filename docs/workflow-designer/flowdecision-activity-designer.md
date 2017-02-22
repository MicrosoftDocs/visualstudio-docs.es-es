---
title: "Dise&#241;ador de actividades FlowDecision | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.FlowDecision.UI"
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades FlowDecision
El nodo <xref:System.Activities.Statements.FlowDecision> es un nodo condicional que proporciona una bifurcación para el flujo de control en una alternativa entre dos, en función de si se ha satisfecho una condición especificada.Si el flujo requiere más de dos bifurcaciones, utilice <xref:System.Activities.Statements.FlowSwitch%601> en su lugar.  
  
## Nodo FlowDecision  
 Utilice el nodo <xref:System.Activities.Statements.FlowDecision> cuando se puedan crear bifurcaciones en dos direcciones a partir del flujo.Un nodo <xref:System.Activities.Statements.FlowDecision> tiene una propiedad <xref:System.Activities.Statements.FlowDecision.Condition%2A> y una clase <xref:System.Activities.Statements.FlowNode> asociadas a cada uno de los dos posibles resultados: <xref:System.Activities.Statements.FlowDecision.True%2A> o <xref:System.Activities.Statements.FlowDecision.False%2A>.Se evalúa <xref:System.Activities.Statements.FlowDecision.Condition%2A> y el valor resultante determina la clase <xref:System.Activities.Statements.FlowNode> siguiente que se va a procesar dentro de <xref:System.Activities.Statements.Flowchart>.  
  
### Utilizar el diseñador FlowDecision  
 El diseñador **FlowDecision** se puede encontrar en la categoría **Diagrama de flujo** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador **FlowDecision** se puede arrastrar desde el **Cuadro de herramientas** y colocar en a la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dentro de un diseñador de actividades **Flowchart**.De esta forma se crea un nodo <xref:System.Activities.Statements.FlowDecision> con la etiqueta **Decision** dentro de la actividad <xref:System.Activities.Statements.Flowchart>.Desplácese con el mouse sobre el diseñador y sobre los identificadores cuadrados **True** y **False** para que aparezcan las dos bifurcaciones.  
  
 Después de arrastrar el diseñador **FlowDecision** y otros diseñadores en el **Diagrama de flujo**, se podrán vincular los nodos entre sí para especificar el orden de ejecución.Para crear un vínculo entre un nodo de origen \(que incluya las bifurcaciones **True** y **False** de **FlowDecision**\) y un nodo de destino, desplácese con el mouse sobre el diseñador del nodo de origen y aparecerán los identificadores cuadrados a cada lado de ellos.Haga clic en uno de los identificadores cuadrados y arrástrelo manteniendo presionado el botón del mouse hasta uno de los identificadores que aparecen de forma similar en torno al nodo de destino cuando desplaza el mouse sobre el mismo.Suelte el botón del mouse y se creará un vínculo entre ambos nodos que quedará representado como una flecha desde el diseñador de origen hasta el diseñador de destino.  
  
 La expresión que indica que se puede escribir <xref:System.Activities.Statements.FlowDecision.Condition%2A> en el cuadro **Condición** de la ventana **Propiedades** si se hace clic donde aparece el texto con la sugerencia "Escriba una expresión de VB".  
  
### Las propiedades FlowDecision  
 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.FlowDecision> y se describe cómo se usan en el diseñador.Estas propiedades se pueden editar en la cuadrícula de propiedades o en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|La condición que determina la ruta de acceso que va a tomar el control de flujo.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|La ruta de acceso que toma el control de flujo si se satisface <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|La ruta de acceso que toma el control de flujo si no se satisface <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|  
  
## Vea también  
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designers.md)   
 [Diagrama de flujo](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)