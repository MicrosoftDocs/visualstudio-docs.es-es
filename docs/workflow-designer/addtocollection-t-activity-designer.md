---
title: "Dise&#241;ador de actividades AddToCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.AddToCollection`1.UI"
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Dise&#241;ador de actividades AddToCollection&lt;T&gt;
El diseñador de actividades **AddToCollection\<T\>** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.AddToCollection%601>.  
  
## Actividad AddToCollection\<T\>  
 La actividad <xref:System.Activities.Statements.AddToCollection%601> agrega un elemento a una colección.  
  
### Utilizar el diseñador de actividades AddToCollection\<T\>  
 El diseñador de actividades **AddToCollection\<T\>** se puede encontrar en la categoría **Colección** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **AddToCollection\<T\>** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se coloquen normalmente las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.Esto crea una actividad <xref:System.Activities.Statements.AddToCollection%601> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de AddToCollection\<Int32\>.\(De forma predeterminada, *TypeArgument* es **Int32**.Se puede cambiar en la cuadrícula de propiedades\). La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **AddToCollection\<T\>** o en el cuadro **DisplayName** de la cuadrícula de propiedades.Es preciso editar las otras propiedades en la cuadrícula de propiedades.  
  
### Propiedades AddToCollection\<T\>  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.AddToCollection%601> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.AddToCollection%601>.El valor predeterminado es AddToCollection\<Int32\>.Pese a que el valor de <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda utilizar uno.|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|El elemento para agregar a Collection\<T\>.Este elemento es de tipo *T*, que a su vez es de tipo *TypeArgument*.Para especificar el elemento, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|La colección a la que se debe agregar el elemento.Esta colección es de tipo **ICollection\<TypeArgument\>**.Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|  
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>.De forma predeterminada, este tipo de *TypeArgument* se establece en **Int32**.Para cambiar el tipo, modifique el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|  
  
## Vea también  
 [Colección](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\> Activity Designer](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)