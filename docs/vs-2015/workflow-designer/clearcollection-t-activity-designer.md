---
title: '&lt;Diseñador de &gt; actividades ClearCollection T | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657019"
---
# <a name="clearcollectionlttgt-activity-designer"></a>&lt;Diseñador de &gt; actividades ClearCollection T
El diseñador de actividades ** \<T> ClearCollection** se utiliza para crear y configurar una <xref:System.Activities.Statements.ClearCollection%601> actividad.

## <a name="the-clearcollectiont-activity"></a>La \<T> actividad ClearCollection
 La actividad <xref:System.Activities.Statements.ClearCollection%601> borra una colección especificada de todos los elementos.

### <a name="using-the-clearcollectiont-activity-designer"></a>Usar el \<T> Diseñador de actividades ClearCollection
 El diseñador de actividades **ClearCollection \<T> ** se puede encontrar en la categoría **colección** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** de. (de forma [!INCLUDE[wfd2](../includes/wfd2-md.md)] alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **ClearCollection \<T> ** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)] , donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.ClearCollection%601> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de ClearCollection \<Int32> . (De forma predeterminada, *TypeArgument* es **Int32**. Esto se puede cambiar en la cuadrícula de propiedades). El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **ClearCollection \<T> ** o en el cuadro **displayName** de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-clearcollectiont-properties"></a>Propiedades de ClearCollection \<T>
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.ClearCollection%601> y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre opcional descriptivo de la actividad <xref:System.Activities.Statements.ClearCollection%601>. El valor predeterminado es ClearCollection \<Int32> . Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Especifica la recopilación que se va a borrar de los elementos. Esta colección es de tipo **ICollection \<TypeArgument> .** Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|True|Especifica el tipo T de los elementos contenidos en <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, este tipo *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|

## <a name="see-also"></a>Consulte también
 [Colección](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)