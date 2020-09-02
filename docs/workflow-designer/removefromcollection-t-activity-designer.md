---
title: Diseñador de flujo de trabajo el &lt; Diseñador de &gt; actividades RemoveFromCollection T
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8af0a0bf8bdf60c8ae9911ef0926cb9e395989a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875584"
---
# <a name="removefromcollectiont-activity-designer"></a>Diseñador de actividad RemoveFromCollection\<T>

El diseñador de actividades ** \<T> RemoveFromCollection** se utiliza para crear y configurar una <xref:System.Activities.Statements.RemoveFromCollection%601> actividad.

## <a name="the-removefromcollectiontactivity"></a>La \<T> actividad RemoveFromCollection

La actividad <xref:System.Activities.Statements.RemoveFromCollection%601> quita un elemento especificado de una colección en particular.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Usar el \<T> Diseñador de actividades RemoveFromCollection

Acceda al diseñador de actividades **RemoveFromCollection \<T> ** en la categoría **colección** del **cuadro de herramientas**.
El diseñador de actividades **RemoveFromCollection \<T> ** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.RemoveFromCollection%601> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de RemoveFromCollection<Int32 \> . El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **RemoveFromCollection \><T** o en el cuadro **displayName** de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-removefromcollectiont-properties"></a>Propiedades de RemoveFromCollection<T \>

En la tabla siguiente se muestran las <xref:System.Activities.Statements.RemoveFromCollection%601> propiedades y se describe cómo se usan en el diseñador:

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.RemoveFromCollection%601>. El valor predeterminado es RemoveFromCollection<Int32 \> .<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Verdadero|Elemento que se va a quitar de la **colección \<T> **. Este elemento es de tipo *T*, que es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Verdadero|Colección de la que se debe quitar el elemento. Esta colección es de tipo **ICollection<TypeArgument \> .** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|Verdadero|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, este tipo *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Un valor que indica si el elemento especificado se quitó de la colección. Para especificar una variable que se vaya a enlazar al resultado, escriba una variable en la cuadrícula de propiedades.|

## <a name="see-also"></a>Consulte también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)