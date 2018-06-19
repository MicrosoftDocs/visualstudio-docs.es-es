---
title: Diseñador de flujo de trabajo - RemoveFromCollection&lt;T&gt; Diseñador de actividad
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6aedee945ab19201406ce26183db4e2f3519263
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31977964"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T > Diseñador de actividad

El **RemoveFromCollection\<T >** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.RemoveFromCollection%601> actividad.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection\<T > actividad
 La actividad <xref:System.Activities.Statements.RemoveFromCollection%601> quita un elemento especificado de una colección en particular.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Usar RemoveFromCollection\<T > Diseñador de actividad
 El **RemoveFromCollection\<T >** Diseñador de actividad puede encontrarse en el **colección** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **Cuadro de herramientas** ficha en el Diseñador de flujo de trabajo (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **RemoveFromCollection\<T >** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, como dentro de un <xref:System.Activities.Statements.Sequence>. Esto crea una <xref:System.Activities.Statements.RemoveFromCollection%601> actividad con el valor predeterminado es <xref:System.Activities.Activity.DisplayName%2A> de RemoveFromCollection < Int32\>. El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado de la **RemoveFromCollection < T\>**  Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T\> propiedades
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.RemoveFromCollection%601> y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.RemoveFromCollection%601>. El valor predeterminado es RemoveFromCollection < Int32\>.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Elemento que se va a agregar a la **colección\<T >**. Este elemento es de tipo *T*, que es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|La colección a la que se debe agregar el elemento. Esta colección es de tipo **ICollection < TypeArgument\>.** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, esto *TypeArgument* tipo está establecido en **Int32**. Para cambiar el tipo, cambie el valor de la *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Un valor que indica si el elemento especificado se quitó de la colección. Para especificar una variable que se vaya a enlazar al resultado, escriba una variable en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)