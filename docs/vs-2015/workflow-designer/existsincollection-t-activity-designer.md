---
title: ExistsInCollection&lt;T&gt; Diseñador de actividad | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 263bbf16c72bab5a42dc0ba1465d4c7062333071
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952832"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection&lt;T&gt; Diseñador de actividad
El **ExistsInCollection\<T >** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.ExistsInCollection%601> actividad.  
  
## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > actividad  
 La actividad <xref:System.Activities.Statements.ExistsInCollection%601> determina si un elemento especificado se encuentra en una colección en particular.  
  
### <a name="using-the-existsincollectiont-activity-designer"></a>Uso de ExistsInCollection\<T > Diseñador de actividad  
 El **ExistsInCollection\<T >** Diseñador de actividad puede encontrarse en el **colección** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el  **Cuadro de herramientas** ficha de [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)  
  
 El **ExistsInCollection\<T >** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie donde se coloquen normalmente las actividades, como dentro de un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.ExistsInCollection%601> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de ExistsInCollection\<Int32 >. (De forma predeterminada, el *TypeArgument* es **Int32**. Se puede cambiar en la cuadrícula de propiedades).  El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **ExistsInCollection\<T >** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.  
  
### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > Propiedades  
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.ExistsInCollection%601> y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.ExistsInCollection%601>. El valor predeterminado es ExistsInCollection\<Int32 >. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|El elemento que se va a agregar a la colección\<T >. Este elemento es de tipo *T* es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión Visual Basic en la cuadrícula de propiedades.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|La colección a la que se debe agregar el elemento. Esta colección es de tipo **ICollection\<TypeArgument >.** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|  
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, esto *TypeArgument* tipo está establecido en **Int32**. Para cambiar el tipo, cambie el valor de la *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Un valor que indica si el elemento especificado existe en la colección. Para especificar una variable a enlazar con el resultado, escriba una variable de Visual Basic en la cuadrícula de propiedades.|  
  
## <a name="see-also"></a>Vea también  
 [colección](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)