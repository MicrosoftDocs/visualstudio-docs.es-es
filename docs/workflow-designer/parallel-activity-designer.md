---
title: "Dise&#241;ador de actividades Parallel | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Parallel.UI"
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades Parallel
La actividad de la clase <xref:System.Activities.Statements.Parallel> ejecuta una colección de actividades secundarias simultáneamente.  
  
## La actividad de la clase Parallel  
 La actividad de la clase <xref:System.Activities.Statements.Parallel> almacena sus actividades secundarias en una colección de la propiedad <xref:System.Activities.Statements.Parallel.Branches%2A>.Use la actividad de la clase <xref:System.Activities.Statements.Parallel> en vez de la actividad de la clase <xref:System.Activities.Statements.Sequence> si alguna de las actividades secundarias se puede quedar inactiva.  
  
 La actividad de la clase <xref:System.Activities.Statements.Parallel> tiene una propiedad <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> que contiene una expresión de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] especificada por el usuario.La actividad <xref:System.Activities.Statements.Parallel> evalúa esta propiedad una vez se complete cada bifurcación.Si se evalúa como **True**, la actividad <xref:System.Activities.Statements.Parallel> se completa sin ejecutar las otras bifurcaciones.Si la propiedad <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> no se evalúa como **True**, la actividad de la clase <xref:System.Activities.Statements.Parallel> se completa una vez que se hayan completado todas sus actividades secundarias.  
  
### Usar el diseñador de actividad Parallel  
 El diseñador de actividad **Parallel** se puede encontrar en la categoría **Flujo de control** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** a la izquierda del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** CTRL\+ALT\+X.\)  
  
 El diseñador de actividad **Parallel** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie del [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se colocan normalmente los diseñadores de actividad, por ejemplo, en un diseñador de actividad **Sequence**.Después de colocarlo en el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], crea una actividad de la clase <xref:System.Activities.Statements.Parallel>, que contiene una propiedad <xref:System.Activities.Activity.DisplayName%2A> de **Parallel**  de forma predeterminada  
  
 Para agregar una colección a la colección de la propiedad <xref:System.Activities.Statements.Parallel.Branches%2A> de la actividad Parallel, arrastre algún otro diseñador de actividad desde el **Cuadro de herramientas** y colóquelo en el triángulo que se encuentra en el diseñador de actividad **Parallel**.Los triángulos rodean las actividades contenidas en las bifurcaciones.Las actividades adicionales se pueden agregar repitiendo este procedimiento.Las actividades se pueden reordenar arrastrándolas y colocándolas en el diseñador de actividad **Parallel**.  
  
### Propiedades de la actividad Parallel en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades de la actividad Parallel y se describe cómo se usan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre para mostrar descriptivo del diseñador de actividades en el encabezado.El valor predeterminado es **Parallel**.De forma opcional, el valor se puede editar en la cuadrícula **Propiedades** o directamente en el encabezado del diseñador de actividad.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Contiene la colección de actividades secundarias que se van a ejecutar.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Se evalúa cuando se completa una bifurcación.Si se evalúa como **True**, se cancelan las bifurcaciones pendientes programadas.Si la propiedad no se establece o se evalúa como **False**, la actividad se completa cuando se hayan completado todas sus actividades secundarias.El valor predeterminado es **null**.|  
  
## Vea también  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)