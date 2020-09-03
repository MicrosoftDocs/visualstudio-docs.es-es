---
title: '&lt;Diseñador de &gt; actividades AddToCollection T | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659209"
---
# <a name="addtocollectionlttgt-activity-designer"></a>&lt;Diseñador de &gt; actividades AddToCollection T
El diseñador de actividades ** \<T> AddToCollection** se utiliza para crear y configurar una <xref:System.Activities.Statements.AddToCollection%601> actividad.

## <a name="the-addtocollectiont-activity"></a>La \<T> actividad AddToCollection
 La actividad <xref:System.Activities.Statements.AddToCollection%601> agrega un elemento a una colección.

### <a name="using-the-addtocollectiont-activity-designer"></a>Usar el \<T> Diseñador de actividades AddToCollection
 El diseñador de actividades **AddToCollection \<T> ** se puede encontrar en la categoría **colección** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** de. (de forma [!INCLUDE[wfd2](../includes/wfd2-md.md)] alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **AddToCollection \<T> ** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)] , donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.AddToCollection%601> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de AddToCollection \<Int32> . (De forma predeterminada, *TypeArgument* es **Int32**. Esto se puede cambiar en la cuadrícula de propiedades). El <xref:System.Activities.Activity.DisplayName%2A> valor se puede editar en el encabezado del diseñador de actividades **AddToCollection \<T> ** o en el cuadro **displayName** de la cuadrícula de propiedades. Es preciso editar las otras propiedades en la cuadrícula de propiedades.

### <a name="the-addtocollectiont-properties"></a>Propiedades de AddToCollection \<T>
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.AddToCollection%601> y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.AddToCollection%601>. El valor predeterminado es AddToCollection \<Int32> . Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Verdadero|Elemento que se va a agregar a la colección \<T> . Este elemento es de tipo *T*, que es de tipo *TypeArgument*. Para especificar el elemento, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Verdadero|La colección a la que se debe agregar el elemento. Esta colección es de tipo **ICollection \<TypeArgument> **. Para especificar la colección, escriba una expresión de Visual Basic en la cuadrícula de propiedades.|
|*TypeArgument*|Verdadero|El tipo T de los elementos que se incluyen en la interfaz <xref:System.Collections.Generic.ICollection%601>. De forma predeterminada, este tipo *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor de *TypeArgument* en el cuadro combinado en la cuadrícula de propiedades.|

## <a name="see-also"></a>Consulte también
 [Collection](../workflow-designer/collection-activity-designers.md) [Diseñador de \<T> actividad](../workflow-designer/addtocollection-t-activity-designer.md) de Collection AddToCollection [ \<T> ClearCollection](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)