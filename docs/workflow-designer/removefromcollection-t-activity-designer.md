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
ms.openlocfilehash: 415d03ffda6bbd2e839354b4f7cb143337ab08c8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891367"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T > Diseñador de actividad

El **RemoveFromCollection\<T >** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.RemoveFromCollection%601> actividad.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection\<T > actividad

La actividad <xref:System.Activities.Statements.RemoveFromCollection%601> quita un elemento especificado de una colección en particular.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Uso de RemoveFromCollection\<T > Diseñador de actividad

Acceso a la **RemoveFromCollection\<T >** Diseñador de actividad en el **colección** categoría de la **cuadro de herramientas**.
El **RemoveFromCollection\<T >** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, como dentro de un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.RemoveFromCollection%601> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de RemoveFromCollection < Int32\>. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado de la **RemoveFromCollection < T\>**  Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T\> propiedades

La tabla siguiente muestra la <xref:System.Activities.Statements.RemoveFromCollection%601> propiedades y se describe cómo se usan en el diseñador:

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.RemoveFromCollection%601>. El valor predeterminado es RemoveFromCollection < Int32\>.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|El elemento que se quitará el **colección\<T >**. Este elemento es de tipo *T*, que es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|La colección que se debe quitar el elemento. Esta colección es de tipo **ICollection < TypeArgument\>.** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, esto *TypeArgument* tipo está establecido en **Int32**. Para cambiar el tipo, cambie el valor de la *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Un valor que indica si el elemento especificado se quitó de la colección. Para especificar una variable que se vaya a enlazar al resultado, escriba una variable en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Colección](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)