---
title: "Dise&#241;ador de actividades ExistsInCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ExistsInCollection`1.UI"
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Dise&#241;ador de actividades ExistsInCollection&lt;T&gt;
El diseñador de actividades **ExistsInCollection\<T\>** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.ExistsInCollection%601>.  
  
## Actividad ExistsInCollection\<T\>  
 La actividad <xref:System.Activities.Statements.ExistsInCollection%601> determina si un elemento especificado se encuentra en una colección en particular.  
  
### Utilizar el diseñador de actividades ExistsInCollection\<T\>  
 El diseñador de actividades **ExistsInCollection\<T\>** se puede encontrar en la categoría **Colección** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **ExistsInCollection\<T\>** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.De esta forma se crea una actividad <xref:System.Activities.Statements.ExistsInCollection%601> con una propiedad predeterminada <xref:System.Activities.Activity.DisplayName%2A> de ExistsInCollection\<Int32\>.\(De forma predeterminada, *TypeArgument* es **Int32**.Se puede cambiar en la cuadrícula de propiedades\).  La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **ExistsInCollection\<T\>** o en el cuadro **DisplayName** de la cuadrícula de propiedades.Es preciso editar las otras propiedades en la cuadrícula de propiedades.  
  
### Propiedades ExistsInCollection\<T\>  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.ExistsInCollection%601> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.ExistsInCollection%601>.El valor predeterminado es ExistsInCollection\<Int32\>.Pese a que el valor de <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda utilizar uno.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|El elemento para agregar a Collection\<T\>.Este elemento es de tipo *T* que a su vez es de tipo *TypeArgument*.Para especificar el elemento, escriba una expresión Visual Basic en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|La colección a la que se debe agregar el elemento.Esta colección es de tipo **ICollection\<TypeArgument\>.**. Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|  
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>.De forma predeterminada, este tipo de *TypeArgument* se establece en **Int32**.Para cambiar el tipo, modifique el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Un valor que indica si el elemento especificado existe en la colección.Para especificar una variable a enlazar con el resultado, escriba una variable de Visual Basic en la cuadrícula de propiedades.|  
  
## Vea también  
 [Colección](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)