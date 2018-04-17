---
title: AddToCollection&lt;T&gt; Diseñador de actividad | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c961c8ab893b1d8b4a2d519d8b9dce27fd6f93c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt; Diseñador de actividad
El **AddToCollection\<T >** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.AddToCollection%601> actividad.

## <a name="the-addtocollectiont-activity"></a>El AddToCollection < T\> actividad
 La actividad <xref:System.Activities.Statements.AddToCollection%601> agrega un elemento a una colección.

### <a name="using-the-addtocollectiont-activity-designer"></a>Mediante el AddToCollection\<T > Diseñador de actividad
 El **AddToCollection\<T >** Diseñador de actividad puede encontrarse en el **colección** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el  **Cuadro de herramientas** pestaña de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **AddToCollection\<T >** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Esto crea una <xref:System.Activities.Statements.AddToCollection%601> actividad con el valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de AddToCollection < Int32\>. (De forma predeterminada, el *TypeArgument* es **Int32**. Se puede cambiar en la cuadrícula de propiedades). El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado de la **AddToCollection < T\>**  Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-addtocollectiont-properties"></a>El AddToCollection < T\> propiedades
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.AddToCollection%601> y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.AddToCollection%601>. El valor predeterminado es AddToCollection < Int32\>. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Elemento que se va a agregar a la colección\<T >. Este elemento es de tipo *T*, que es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|La colección a la que se debe agregar el elemento. Esta colección es de tipo **ICollection < TypeArgument\>**. Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, esto *TypeArgument* tipo está establecido en **Int32**. Para cambiar el tipo, cambie el valor de la *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > Diseñador de actividad](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)