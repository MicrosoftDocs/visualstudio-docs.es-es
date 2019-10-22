---
title: Diseñador de actividades Diseñador de flujo de trabajo-ClearCollection <T>
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4808c046c4da23bc5c95d3978965afd938962f5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650691"
---
# <a name="clearcollectiont-activity-designer"></a>Diseñador de actividad de ClearCollection \<T >

El diseñador de actividad **ClearCollection \<T >** se usa para crear y configurar una actividad <xref:System.Activities.Statements.ClearCollection%601>.

## <a name="the-clearcollectiont-activity"></a>Actividad de > de \<T de ClearCollection

La actividad <xref:System.Activities.Statements.ClearCollection%601> borra una colección especificada de todos los elementos.

### <a name="using-the-clearcollectiont-activity-designer"></a>Usar el diseñador de actividades ClearCollection \<T >

El diseñador de actividades **ClearCollection \<T >** se puede encontrar en la categoría **colección** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** +**Alt** +**X**.

El diseñador de actividades **ClearCollection \<T >** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de la diseñador de flujo de trabajo dondequiera que se coloquen las actividades, como en una <xref:System.Activities.Statements.Sequence>. Al quitar el diseñador de actividad, se crea una actividad <xref:System.Activities.Statements.ClearCollection%601> con un <xref:System.Activities.Activity.DisplayName%2A> predeterminado de ClearCollection < Int32 \>. (De forma predeterminada, *TypeArgument* es **Int32**. TypeArgument se puede cambiar en la cuadrícula de propiedades). El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **ClearCollection < t \>** o en el cuadro **displayName** de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-clearcollectiont-properties"></a>Propiedades de > del \<T ClearCollection

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.ClearCollection%601> y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.ClearCollection%601>. El valor predeterminado es ClearCollection < Int32 \>. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Especifica la recopilación que se va a borrar de los elementos. Esta colección es de tipo **ICollection \<TypeArgument >.** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|True|Especifica el tipo T de los elementos contenidos en <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, este tipo *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)