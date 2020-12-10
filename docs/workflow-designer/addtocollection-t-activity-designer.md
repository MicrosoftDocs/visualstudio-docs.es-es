---
title: '&lt;Diseñador de &gt; actividades AddToCollection T'
description: Obtenga información sobre cómo <T> se usa el diseñador de actividades AddToCollection para crear y configurar una <T> actividad AddToCollection en diseñador de flujo de trabajo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1592eab528f2312a9ad90dec02354814d6a81c3
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993255"
---
# <a name="addtocollectiont-activity-designer"></a>Diseñador de actividad AddToCollection\<T>

El diseñador de actividades **\<T> AddToCollection** se utiliza para crear y configurar una <xref:System.Activities.Statements.AddToCollection%601> actividad.

## <a name="the-addtocollectiont-activity"></a>La \<T> actividad AddToCollection

La actividad <xref:System.Activities.Statements.AddToCollection%601> agrega un elemento a una colección.

### <a name="using-the-addtocollectiont-activity-designer"></a>Usar el \<T> Diseñador de actividades AddToCollection

El diseñador de actividades **AddToCollection \<T>** se puede encontrar en la categoría **colección** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

El diseñador de actividades **AddToCollection \<T>** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo cada vez que se colocan las actividades, como en una <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividades **\<T> AddToCollection** , se crea una <xref:System.Activities.Statements.AddToCollection%601> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de AddToCollection<Int32 \> . (De forma predeterminada, *TypeArgument* es **Int32**. TypeArgument se puede cambiar en la cuadrícula de propiedades). El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **AddToCollection \><T** o en el cuadro **displayName** de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-addtocollectiont-properties"></a>Propiedades de AddToCollection \<T>

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.AddToCollection%601> y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.AddToCollection%601>. El valor predeterminado es AddToCollection<Int32 \> . Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Verdadero|Elemento que se va a agregar a la colección \<T> . Este elemento es de tipo *T*, que es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Verdadero|La colección a la que se debe agregar el elemento. Esta colección es de tipo **ICollection<TypeArgument \>**. Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|Verdadero|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, este tipo *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|

## <a name="see-also"></a>Consulte también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [Diseñador de actividad\<T> AddToCollection](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
