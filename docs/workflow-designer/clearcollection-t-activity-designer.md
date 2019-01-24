---
title: Diseñador de flujo de trabajo - ClearCollection<T> Diseñador de actividad
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ba2fbaf22f7a27d4984ab49e4e8f93897da668ac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986536"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T > Diseñador de actividad

El **ClearCollection\<T >** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.ClearCollection%601> actividad.

## <a name="the-clearcollectiont-activity"></a>ClearCollection\<T > actividad

La actividad <xref:System.Activities.Statements.ClearCollection%601> borra una colección especificada de todos los elementos.

### <a name="using-the-clearcollectiont-activity-designer"></a>Uso de ClearCollection\<T > Diseñador de actividad

El **ClearCollection\<T >** Diseñador de actividad puede encontrarse en el **colección** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el  **Cuadro de herramientas** ficha del Diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** desde el **vista** menús o presione **Ctrl**+**Alt** + **X**.

El **ClearCollection\<T >** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se colocan las actividades, por ejemplo, dentro de un <xref:System.Activities.Statements.Sequence>. Al colocar el Diseñador de actividad se crea un <xref:System.Activities.Statements.ClearCollection%601> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de ClearCollection < Int32\>. (De forma predeterminada, el *TypeArgument* es **Int32**. TypeArgument puede cambiarse en la cuadrícula de propiedades.) El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **ClearCollection < T\>**  Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-clearcollectiont-properties"></a>ClearCollection\<T > Propiedades

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.ClearCollection%601> y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.ClearCollection%601>. El valor predeterminado es ClearCollection < Int32\>. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Especifica la colección que se va a borrar de los elementos. Esta colección es de tipo **ICollection\<TypeArgument >.** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|True|Especifica el tipo T de los elementos contenidos en <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, esto *TypeArgument* tipo está establecido en **Int32**. Para cambiar el tipo, cambie el valor de la *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)