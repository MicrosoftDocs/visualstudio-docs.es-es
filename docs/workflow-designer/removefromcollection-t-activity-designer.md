---
title: "Dise&#241;ador de actividades RemoveFromCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.RemoveFromCollection`1.UI"
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Dise&#241;ador de actividades RemoveFromCollection&lt;T&gt;
El diseñador de actividades **RemoveFromCollection\<T\>** se utiliza para crear y configurar una actividad <xref:System.Activities.Statements.RemoveFromCollection%601>.  
  
## Actividad RemoveFromCollection\<T\>  
 La actividad <xref:System.Activities.Statements.RemoveFromCollection%601> quita un elemento especificado de una colección en particular.  
  
### Utilizar el diseñador de actividades RemoveFromCollection\<T\>  
 El diseñador de actividades **RemoveFromCollection\<T\>** se puede encontrar en la categoría **Colección** del **Cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **Cuadro de herramientas** de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. \(De forma alternativa, seleccione **Barra de herramientas** del menú **Ver** o CTRL\+ALT\+X\).  
  
 El diseñador de actividades **RemoveFromCollection\<T\>** se puede arrastrar desde el **Cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], donde se suelan colocar las actividades, como en una clase <xref:System.Activities.Statements.Sequence>.De esta forma se crea una actividad <xref:System.Activities.Statements.RemoveFromCollection%601> con una propiedad predeterminada <xref:System.Activities.Activity.DisplayName%2A> de RemoveFromCollection\<Int32\>.La propiedad <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **RemoveFromCollection\<T\>** o en el cuadro **DisplayName** de la cuadrícula de propiedades.Es preciso editar las otras propiedades en la cuadrícula de propiedades.  
  
### Propiedades RemoveFromCollection\<T\>  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.RemoveFromCollection%601> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|----------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.RemoveFromCollection%601>.El valor predeterminado es RemoveFromCollection\<Int32\>.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|El elemento para agregar a **Collection\<T\>**.Este elemento es de tipo *T*, que a su vez es de tipo *TypeArgument*.Para especificar el elemento, escriba una expresión Visual Basic en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|La colección a la que se debe agregar el elemento.Esta colección es de tipo **ICollection\<TypeArgument\>.**. Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|  
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>.De forma predeterminada, este tipo de *TypeArgument* se establece en **Int32**.Para cambiar el tipo, modifique el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Un valor que indica si el elemento especificado se quitó de la colección.Para especificar una variable que se vaya a enlazar al resultado, escriba una variable en la cuadrícula de propiedades.|  
  
## Vea también  
 [Colección](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)