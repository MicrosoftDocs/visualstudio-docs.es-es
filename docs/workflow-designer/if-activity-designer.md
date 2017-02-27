---
title: "Dise&#241;ador de actividades If | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.If.UI"
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Dise&#241;ador de actividades If
La actividad <xref:System.Activities.Statements.If> evalúa una condición y ejecuta una actividad según los resultados de esa evaluación.Esta actividad es muy útil cuando se utiliza un estilo de modelado por procedimientos de programación.Una actividad <xref:System.Activities.Statements.If> puede estar anidada en una actividad <xref:System.Activities.Statements.Sequence> o en una actividad <xref:System.Activities.Statements.Parallel>, por ejemplo.Si está utilizando una actividad <xref:System.Activities.Statements.Flowchart>, plantéese utilizar una actividad <xref:System.Activities.Statements.FlowDecision> en su lugar.  
  
## Propiedades If en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.If> más útiles y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|La condición que determina qué actividad secundaria se va a ejecutar.Para establecer <xref:System.Activities.Statements.If.Condition%2A>, escriba una expresión de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en el cuadro **Condition** en el diseñador de actividades **If** o en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|La actividad que se va a ejecutar si <xref:System.Activities.Statements.If.Condition%2A> es **false**.Para agregar una actividad que ejecute la bifurcación <xref:System.Activities.Statements.If.Else%2A>, coloque una actividad del **Cuadro de herramientas** en el cuadro **Else** en el diseñador de actividades **If** donde aparezca el texto con la sugerencia "Coloque la actividad aquí".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|La actividad que se va a ejecutar si el valor de propiedad <xref:System.Activities.Statements.If.Condition%2A> es **true**.Para agregar una actividad que ejecute la bifurcación de la propiedad <xref:System.Activities.Statements.If.Then%2A>, coloque una actividad del **Cuadro de herramientas** en el cuadro **Then** del diseñador de actividad **If** con el texto de la sugerencia "Coloque la actividad aquí".|  
  
## Vea también  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)