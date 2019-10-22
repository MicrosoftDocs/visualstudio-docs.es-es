---
title: Diseñador de actividades de Diseñador de flujo de trabajo-ParallelForEach &lt;T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68cd543ed41408e7510708367c8e539c0702ea1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650087"
---
# <a name="parallelforeach-activity-designer"></a>Diseñador de actividades ParallelForEach

La actividad <xref:System.Activities.Statements.ParallelForEach%601> enumera los elementos de una colección y ejecuta una instrucción incrustada para cada elemento de la colección en paralelo, la cual se presenta de forma asincrónica en el mismo subproceso. Utilice esta actividad de control de flujo en lugar de la actividad <xref:System.Activities.Statements.Sequence> si se desea que las actividades secundarias de esta actividad pasen a estado inactivo.

La actividad <xref:System.Activities.Statements.ParallelForEach%601> tiene una propiedad <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> que contiene una expresión Visual Basic especificada por el usuario. La actividad <xref:System.Activities.Statements.ParallelForEach%601> evalúa esta propiedad una vez se complete cada bifurcación. Si se evalúa como **true**, la actividad <xref:System.Activities.Statements.ParallelForEach%601> se completa sin ejecutar las otras bifurcaciones. Si el <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> no se evalúa como **true**, la actividad de <xref:System.Activities.Statements.ParallelForEach%601> se completa cuando se han completado todas sus actividades secundarias.

## <a name="the-parallelforeacht-activity"></a>Actividad de \> ParallelForEach < T

<xref:System.Activities.Statements.ParallelForEach%601> enumera sus valores y programa la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> para cada valor que enumera. Solo programa la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La forma en que efectúe el cuerpo la ejecución depende de si <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pasa a estado inactivo.

Si la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> no pasa a estado inactivo, se ejecuta en orden inverso porque las actividades programadas se administran como una pila, la última actividad programada se ejecuta primero. Por ejemplo, si tiene una colección de {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> y usa **WriteLine** como cuerpo para escribir el valor. Tiene 4, 3, 2, 1 impresos en la consola. Esto se debe a que **WriteLine** no entra en estado inactivo, por lo que después de que se hayan programado 4 actividades **WriteLine** , se ejecutan mediante un comportamiento de pila (primero en salir).

Pero si tiene actividades en la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> que pueden pasar a estado inactivo, como una actividad <xref:System.ServiceModel.Activities.Receive> o <xref:System.Activities.Statements.Delay>, A continuación no hay necesidad de esperarlos para completarse. <xref:System.Activities.Statements.ParallelForEach%601> va a la siguiente actividad de cuerpo programada e intenta ejecutarla. Si esa actividad también pasa a estado inactivo, <xref:System.Activities.Statements.ParallelForEach%601> vuelve a desplazarse hasta la siguiente actividad del cuerpo.

### <a name="using-the-parallelforeacht-activity-designer"></a>Usar el diseñador de actividades ParallelForEach \<T >

Acceda al diseñador de actividad **ParallelForEach \<T >** en la categoría **flujo de control** del **cuadro de herramientas**.

El diseñador de actividades **ParallelForEach \<T >** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de la diseñador de flujo de trabajo, donde los diseñadores de actividad se colocan normalmente, por ejemplo, dentro de una actividad **Sequence** . generador. Después de colocarlo en el Diseñador de flujo de trabajo, crea una actividad <xref:System.Activities.Statements.ParallelForEach%601>, que de forma predeterminada contiene un <xref:System.Activities.Activity.DisplayName%2A> de **ParallelForEach < Int32 \>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T \> propiedades del Diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.ParallelForEach%601> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre para mostrar descriptivo del diseñador de actividades en el encabezado. El valor predeterminado es **ParallelForEach \<Int32 >** . El valor se puede editar opcionalmente en la cuadrícula de **propiedades** o directamente en el encabezado del diseñador de actividad.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|La actividad que se va a ejecutar para cada elemento en la colección. Para agregar la actividad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, coloque una actividad del cuadro de herramientas en el cuadro **Body** del diseñador de actividades de **ParallelForEach \<T >** con el texto de la sugerencia "Coloque la actividad aquí".|
|**TypeArgument**|True|Tipo de los elementos de la colección de <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> especificados por el parámetro genérico *t*. De forma predeterminada, **TypeArgument** se establece en **Int32**. Para cambiar el tipo T en el diseñador de actividades **ParallelForEach < T \>** , cambie el valor del cuadro combinado **TypeArgument** en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|La colección de elementos en la que se va a iterar. Para establecer el <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, escriba una expresión de Visual Basic en el cuadro **valores** del diseñador de actividades **ForEach < t \>** en el cuadro con el texto de la sugerencia "Escriba una expresión de VB" o en el cuadro **valores** de la ventana **propiedades** .|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Se evalúa cuando se completa cada iteración. Si se evalúa como true, se cancelan las operaciones programadas pendientes. Si no se establece esta propiedad, se ejecutan todas las instrucciones programadas hasta su compleción.|

De forma predeterminada, el iterador del bucle se denomina elemento. Puede cambiar el nombre de la variable de iterador en el cuadro **foreach** en **ParallelForEach \<T >** diseñador de actividad. El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Vea también

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)