---
title: Diseñador de flujo de trabajo - ParallelForEach&lt;T&gt; Diseñador de actividad
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c62918811ba91fe9c30f60e930ce77a640959d0f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846348"
---
# <a name="parallelforeach-activity-designer"></a>Diseñador de actividades ParallelForEach

La actividad <xref:System.Activities.Statements.ParallelForEach%601> enumera los elementos de una colección y ejecuta una instrucción incrustada para cada elemento de la colección en paralelo, la cual se presenta de forma asincrónica en el mismo subproceso. Utilice esta actividad de control de flujo en lugar de la actividad <xref:System.Activities.Statements.Sequence> si se desea que las actividades secundarias de esta actividad pasen a estado inactivo.

El <xref:System.Activities.Statements.ParallelForEach%601> actividad tiene un <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> propiedad que contiene un usuario especifica la expresión de Visual Basic. La actividad <xref:System.Activities.Statements.ParallelForEach%601> evalúa esta propiedad una vez se complete cada bifurcación. Si se evalúa como **true**, la <xref:System.Activities.Statements.ParallelForEach%601> actividad se completa sin ejecutar las demás ramas. Si el <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> no se evalúa como **true**, la <xref:System.Activities.Statements.ParallelForEach%601> actividad se completa cuando se hayan completado todas sus actividades secundarias.

## <a name="the-parallelforeacht-activity"></a>El ParallelForEach < T\> actividad

<xref:System.Activities.Statements.ParallelForEach%601> enumera sus valores y programa la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> para cada valor que enumera. Solo programa la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La forma en que efectúe el cuerpo la ejecución depende de si <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pasa a estado inactivo.

Si la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> no pasa a estado inactivo, se ejecuta en orden inverso porque las actividades programadas se administran como una pila, la última actividad programada se ejecuta primero. Por ejemplo, si tiene una colección de {1,2,3,4}en <xref:System.Activities.Statements.ParallelForEach%601> y usar un **WriteLine** como cuerpo para escribir el valor. en la consola, tendrá impreso 4, 3, 2, 1. Esto es porque **WriteLine** no pasa a estado inactivo, después de 4 **WriteLine** se programaron las actividades, estas se ejecutan utilizando un comportamiento stack (primero en último fuera).

Pero si tiene actividades en la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> que pueden pasar a estado inactivo, como una actividad <xref:System.ServiceModel.Activities.Receive> o <xref:System.Activities.Statements.Delay>, A continuación no hay necesidad de esperarlos para completarse. <xref:System.Activities.Statements.ParallelForEach%601> va a la siguiente actividad de cuerpo programada e intenta ejecutarla. Si esa actividad también pasa a estado inactivo, <xref:System.Activities.Statements.ParallelForEach%601> vuelve a desplazarse hasta la siguiente actividad del cuerpo.

### <a name="using-the-parallelforeacht-activity-designer"></a>Mediante el ParallelForEach\<T > Diseñador de actividad

Acceso a la **ParallelForEach\<T >** Diseñador de actividad en el **flujo de Control** categoría de la **cuadro de herramientas**.

El **ParallelForEach\<T >** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde normalmente se colocan los diseñadores de actividad, para ejemplo, dentro de un **secuencia** Diseñador de actividad. Después de colocarlo en el Diseñador de flujo de trabajo, crea un <xref:System.Activities.Statements.ParallelForEach%601> actividad, que de forma predeterminada, contiene un <xref:System.Activities.Activity.DisplayName%2A> de **ParallelForEach < Int32\>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T\> propiedades en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.ParallelForEach%601> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre para mostrar descriptivo del diseñador de actividades en el encabezado. El valor predeterminado es **ParallelForEach\<Int32 >**. El valor se puede editar, opcionalmente, en el **propiedades** cuadrícula o directamente en el encabezado del Diseñador de actividad.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|La actividad que se va a ejecutar para cada elemento en la colección. Para agregar la <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> actividad, coloque una actividad en el cuadro de herramientas en el **cuerpo** cuadro en el **ParallelForEach\<T >** Diseñador de actividad con el texto de la sugerencia "Coloque la actividad aquí".|
|**TypeArgument**|True|El tipo de los elementos de la <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> colección especificada por el parámetro genérico *T*. De forma predeterminada, **TypeArgument** está establecido en **Int32**. Para cambiar el tipo T en el **ParallelForEach < T\>**  Diseñador de actividad, cambie el valor de la **TypeArgument** cuadro combinado en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|La colección de elementos en la que se va a iterar. Para establecer el <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, escriba una expresión de Visual Basic en el **valores** cuadro en el **ForEach < T\>**  Diseñador de actividad en el cuadro de texto con la sugerencia "Escriba una expresión de VB" o en  **Valores** cuadro en el **propiedades** ventana.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Se evalúa cuando se completa cada iteración. Si se evalúa como true, se cancelan las operaciones programadas pendientes. Si no se establece esta propiedad, se ejecutan todas las instrucciones programadas hasta su compleción.|

De forma predeterminada, el iterador del bucle se denomina elemento. Puede cambiar el nombre de la variable de iterador en el **ForEach** cuadro **ParallelForEach\<T >** Diseñador de actividad. El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Vea también

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)