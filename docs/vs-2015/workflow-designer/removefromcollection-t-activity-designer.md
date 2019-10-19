---
title: Diseñador de actividad de RemoveFromCollection &lt;T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ac088c6e5710fcd1b7c401402ad473488f89524
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672574"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>Diseñador de actividad de RemoveFromCollection &lt;T &gt;
El diseñador de actividad **RemoveFromCollection \<T >** se usa para crear y configurar una actividad <xref:System.Activities.Statements.RemoveFromCollection%601>.

## <a name="the-removefromcollectiont-activity"></a>Actividad de > de \<T de RemoveFromCollection
 La actividad <xref:System.Activities.Statements.RemoveFromCollection%601> quita un elemento especificado de una colección en particular.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Usar el diseñador de actividades RemoveFromCollection \<T >
 El diseñador de actividades **RemoveFromCollection \<T >** se puede encontrar en la categoría **colección** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** de [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione **barra de herramientas** de el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **RemoveFromCollection \<T >** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de la [!INCLUDE[wfd2](../includes/wfd2-md.md)], donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.RemoveFromCollection%601> con un <xref:System.Activities.Activity.DisplayName%2A> predeterminado de RemoveFromCollection \<Int32 >. El valor <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades de **RemoveFromCollection \<T >** o en el cuadro **displayName** de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-removefromcollectiont-properties"></a>Propiedades de > del \<T RemoveFromCollection
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.RemoveFromCollection%601> y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|El nombre descriptivo opcional de la actividad de la clase <xref:System.Activities.Statements.RemoveFromCollection%601>. El valor predeterminado es RemoveFromCollection \<Int32 >.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Elemento que se va a agregar a la **colección \<T >** . Este elemento es de tipo *T*, que es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|La colección a la que se debe agregar el elemento. Esta colección es de tipo **ICollection \<TypeArgument >.** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|True|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, este tipo *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Un valor que indica si el elemento especificado se quitó de la colección. Para especificar una variable que se vaya a enlazar al resultado, escriba una variable en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md)