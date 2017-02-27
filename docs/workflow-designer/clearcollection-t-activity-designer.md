---
title: "Dise&#241;ador de actividades ClearCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ClearCollection`1.UI"
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Dise&#241;ador de actividades ClearCollection&lt;T&gt;
El diseñador de actividades **ClearCollection\<T\>** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.ClearCollection%601>.  
  
## Actividad ClearCollection\<T\>  
 La actividad <xref:System.Activities.Statements.ClearCollection%601> borra una colección especificada de todos los elementos.  
  
### Utilizar el diseñador de actividades ClearCollection\<T\>  
 El diseñador de actividades **ClearCollection\<T\>** se puede encontrar en la categoría **Colección** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **ClearCollection\<T\>** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se suelan colocar las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.Esto crea una actividad <xref:System.Activities.Statements.ClearCollection%601> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de ClearCollection\<Int32\>.\(De forma predeterminada, *TypeArgument* es **Int32**.Se puede cambiar en la cuadrícula de propiedades\). El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **ClearCollection\<T\>** o en el cuadro **DisplayName** de la cuadrícula de propiedades.Es preciso editar las otras propiedades en la cuadrícula de propiedades.  
  
### Propiedades ClearCollection\<T\>  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.ClearCollection%601> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.ClearCollection%601>.El valor predeterminado es ClearCollection\<Int32\>.Pese a que el valor de <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda utilizar uno.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Especifica la recopilación que se va a borrar de los elementos.Esta colección es de tipo **ICollection\<TypeArgument\>.**. Para especificar la colección, escriba una expresión Visual Basic en la cuadrícula de propiedades.|  
|*TypeArgument*|True|Especifica el tipo T de los elementos contenidos en <xref:System.Collections.Generic.ICollection%601>.De forma predeterminada, este tipo de *TypeArgument* se establece en **Int32**.Para cambiar el tipo, modifique el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|  
  
## Vea también  
 [Colección](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)