---
title: Diseñador de flujo de trabajo - ExistsInCollection&lt;T&gt; Diseñador de actividad
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 59ec7e9df4088c21820fa5fec319ab3e4ac10f78
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853264"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T > Diseñador de actividad

El **ExistsInCollection\<T >** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.ExistsInCollection%601> actividad.

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > actividad

La actividad <xref:System.Activities.Statements.ExistsInCollection%601> determina si un elemento especificado se encuentra en una colección en particular.

### <a name="using-the-existsincollectiont-activity-designer"></a>Uso de ExistsInCollection\<T > Diseñador de actividad

El **ExistsInCollection\<T >** Diseñador de actividad puede encontrarse en el **colección** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el  **Cuadro de herramientas** ficha del Diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** desde el **vista** menús o presione **Ctrl**+**Alt** + **X**.

El **ExistsInCollection\<T >** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.ExistsInCollection%601> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de ExistsInCollection < Int32\>. (De forma predeterminada, el *TypeArgument* es **Int32**. Se puede cambiar en la cuadrícula de propiedades).  El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **ExistsInCollection < T\>**  Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > Propiedades

La tabla siguiente muestra la <xref:System.Activities.Statements.ExistsInCollection%601> propiedades y se describe cómo se usan en el diseñador:

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.ExistsInCollection%601>. El valor predeterminado es ExistsInCollection < Int32\>. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Elemento que se va a buscar en la colección\<T >. Este elemento es de tipo *T*, que es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión Visual Basic en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|La colección en el que se va a comprobar si existe el elemento. Esta colección es de tipo **ICollection < TypeArgument\>.** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, esto *TypeArgument* tipo está establecido en **Int32**. Para cambiar el tipo, cambie el valor de la *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Un valor que indica si el elemento especificado existe en la colección. Para especificar una variable a enlazar con el resultado, escriba una variable de Visual Basic en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)