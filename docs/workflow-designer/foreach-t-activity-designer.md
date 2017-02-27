---
title: "Dise&#241;ador de actividades ForEach&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ForEach`1.UI"
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Dise&#241;ador de actividades ForEach&lt;T&gt;
La actividad <xref:System.Activities.Statements.ForEach%601> ejecuta la actividad que se incluye en su propiedad <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada elemento en una colección <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.  
  
## Propiedades ForEach\<T\> en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las propiedades de actividades <xref:System.Activities.Statements.ForEach%601> más útiles y se describe cómo se usan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo de la actividad <xref:System.Activities.Statements.ForEach%601>.El valor predeterminado es ForEach\<Int32\>.Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|La colección de elementos en la que se va a iterar.Para establecer la propiedad <xref:System.Activities.Statements.ForEach%601.Values%2A>, escriba una expresión de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en el cuadro **Valores** del diseñador de actividad **ForEach\<T\>** o en la cuadrícula de propiedades.|  
|*TypeArgument*|True|El tipo de elementos en la colección <xref:System.Activities.Statements.ForEach%601.Values%2A> que ha especificado el parámetro genérico *T*.De manera predeterminada, *TypeArgument* se establece en **Int32**.Para cambiar el tipo, modifique el valor del cuadro combinado *TypeArgument* en la cuadrícula de propiedades.|  
  
 De forma predeterminada, el iterador del bucle se denomina **item**.Puede cambiar el nombre de la variable de iterador en el diseñador de actividades <xref:System.Activities.Statements.ForEach%601>.El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ForEach%601>.  
  
## Vea también  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)