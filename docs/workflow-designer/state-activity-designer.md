---
title: "Dise&#241;ador de actividad State | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.State.UI"
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "sdanie"
manager: "erikre"
---
# Dise&#241;ador de actividad State
<xref:System.Activities.Statements.State> representa un estado en el que una máquina de estados puede estar.  
  
## Usar el diseñador de actividades State  
 Para agregar un <xref:System.Activities.Statements.State> a un flujo de trabajo, arrastre la actividad **State** desde la sección **Máquina de estados** del **Cuadro de herramientas** y colóquela en una actividad <xref:System.Activities.Statements.StateMachine> en la superficie de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Una actividad <xref:System.Activities.Statements.State> se puede colocar sobre <xref:System.Activities.Statements.StateMachine> y agregar transiciones más adelante; o se puede crear una transición mientras se coloca la actividad <xref:System.Activities.Statements.State>.Para agregar una actividad <xref:System.Activities.Statements.State> y crear una transición en un paso, arrastre una actividad **State** desde la sección **Máquina de estados** del **Cuadro de herramientas** y mantenga el mouse sobre otro estado en el diseñador de flujo de trabajo.Cuando el <xref:System.Activities.Statements.State> arrastrado está sobre a otro <xref:System.Activities.Statements.State>, aparecerán cuatro triángulos alrededor del otro <xref:System.Activities.Statements.State>.Si <xref:System.Activities.Statements.State> se coloca sobre uno de los cuatro triángulos, se agrega a la máquina de estados y se crea una transición desde el <xref:System.Activities.Statements.State> de origen al <xref:System.Activities.Statements.State> de destino colocado.Para obtener más información, vea [Transición](../workflow-designer/transition-activity-designer.md).  
  
### Propiedades de la actividad State en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades de <xref:System.Activities.Statements.State> que se pueden establecer mediante el diseñador de flujo de trabajo y se describe cómo se usan en el diseñador.Algunas de estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas en la superficie del diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.State> en el encabezado.El valor predeterminado es **State**.El valor se puede editar en la cuadrícula de propiedades o directamente en el encabezado del diseñador de actividades.<xref:System.Activities.Statements.State.DisplayName%2A> se usa en la ruta de navegación que se muestra en la parte superior del diseñador de flujo de trabajo.<br /><br /> Aunque el valor de propiedad <xref:System.Activities.Statements.State.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica la acción que se produce cuando se entra en este estado.Cuando se expande la actividad <xref:System.Activities.Statements.State>, este valor se puede establecer arrastrando una actividad del **Cuadro de herramientas** y colocándola sobre la sección **Entrada** del estado.|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|Especifica la acción que se produce cuando se sale de este estado.Cuando se expande la actividad <xref:System.Activities.Statements.State>, este valor se puede establecer arrastrando una actividad del **Cuadro de herramientas** y colocándola sobre la sección **Salida** del estado.|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Muestra las transiciones posibles que se originan desde <xref:System.Activities.Statements.State>.Cada elemento de la lista tiene un vínculo a la <xref:System.Activities.Statements.Transition> asociada y el <xref:System.Activities.Statements.State> de destino.Haciendo clic en el vínculo cambiará el diseñador a una vista expandida de <xref:System.Activities.Statements.Transition> o de <xref:System.Activities.Statements.State>.|  
  
## Vea también  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [Transición](../workflow-designer/transition-activity-designer.md)