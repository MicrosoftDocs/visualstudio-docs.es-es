---
title: Diseñador de flujo de trabajo el &lt; Diseñador de &gt; actividades ExistsInCollection T
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b48bb11e2aac9d542a07551df62d710c41596d28
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875662"
---
# <a name="existsincollectiont-activity-designer"></a>Diseñador de actividad ExistsInCollection\<T>

El diseñador de actividades ** \<T> ExistsInCollection** se utiliza para crear y configurar una <xref:System.Activities.Statements.ExistsInCollection%601> actividad.

## <a name="the-existsincollectiont-activity"></a>La \<T> actividad ExistsInCollection

La actividad <xref:System.Activities.Statements.ExistsInCollection%601> determina si un elemento especificado se encuentra en una colección en particular.

### <a name="using-the-existsincollectiont-activity-designer"></a>Usar el \<T> Diseñador de actividades ExistsInCollection

El diseñador de actividades **ExistsInCollection \<T> ** se puede encontrar en la categoría **colección** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** de diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

El diseñador de actividades **ExistsInCollection \<T> ** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.ExistsInCollection%601> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de ExistsInCollection<Int32 \> . (De forma predeterminada, *TypeArgument* es **Int32**. Se puede cambiar en la cuadrícula de propiedades).  El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **ExistsInCollection \><T** o en el cuadro **displayName** de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-existsincollectiont-properties"></a>Propiedades de ExistsInCollection \<T>

En la tabla siguiente se muestran las <xref:System.Activities.Statements.ExistsInCollection%601> propiedades y se describe cómo se usan en el diseñador:

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.ExistsInCollection%601>. El valor predeterminado es ExistsInCollection<Int32 \> . Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Elemento que se va a buscar en la colección \<T> . Este elemento es de tipo *T*, que es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión Visual Basic en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Colección en la que se va a comprobar si el elemento existe. Esta colección es de tipo **ICollection<TypeArgument \> .** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, este tipo *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Un valor que indica si el elemento especificado existe en la colección. Para especificar una variable a enlazar con el resultado, escriba una variable de Visual Basic en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)