---
title: "Dise&#241;ador de actividades Throw | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Throw.UI"
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Dise&#241;ador de actividades Throw
El diseñador de actividades **Throw** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.Throw>.  
  
## Actividad Throw  
 La actividad <xref:System.Activities.Statements.Throw> produce una excepción.  
  
### Utilizar el diseñador de actividades Throw  
 El diseñador de actividades **Throw** se puede encontrar en la categoría **Control de errores** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** en el menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **Throw** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se suelan colocar las actividades, como en un <xref:System.Activities.Statements.Sequence>.Esto crea una actividad <xref:System.Activities.Statements.Throw> con un valor **DisplayName** predeterminado de Throw.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **Throw** o en el cuadro **DisplayName** de la cuadrícula de propiedades.La propiedad <xref:System.Activities.Statements.Throw.Exception%2A> se debe editar en la cuadrícula de propiedades.  
  
### Propiedades Throw  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Throw> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.Throw>.El valor predeterminado es Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Excepción que se va a producir.Esta excepción debe derivar de <xref:System.Exception>.Para especificar la excepción, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|  
  
## Vea también  
 [Colección](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw Activity Designer](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)