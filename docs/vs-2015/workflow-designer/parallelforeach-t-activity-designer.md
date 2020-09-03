---
title: '&lt;Diseñador de &gt; actividades ParallelForEach T | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c659e941a8503a0d5ff601fea23fcec69b2bbcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672613"
---
# <a name="parallelforeachlttgt-activity-designer"></a>&lt;Diseñador de &gt; actividades ParallelForEach T
La actividad <xref:System.Activities.Statements.ParallelForEach%601> enumera los elementos de una colección y ejecuta una instrucción incrustada para cada elemento de la colección en paralelo, la cual se presenta de forma asincrónica en el mismo subproceso. Utilice esta actividad de control de flujo en lugar de la actividad <xref:System.Activities.Statements.Sequence> si se desea que las actividades secundarias de esta actividad pasen a estado inactivo.

 La actividad <xref:System.Activities.Statements.ParallelForEach%601> tiene una propiedad <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> que contiene a una expresión [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] especificada por el usuario. La actividad <xref:System.Activities.Statements.ParallelForEach%601> evalúa esta propiedad una vez se complete cada bifurcación. Si se evalúa como **true**, la actividad se <xref:System.Activities.Statements.ParallelForEach%601> completa sin ejecutar las otras bifurcaciones. Si no <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> se evalúa como **true**, la actividad se <xref:System.Activities.Statements.ParallelForEach%601> completa cuando se han completado todas sus actividades secundarias.

## <a name="the-parallelforeacht-activity"></a>La \<T> actividad ParallelForEach
 <xref:System.Activities.Statements.ParallelForEach%601> enumera sus valores y programa el <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> para cada valor que enumera. Solo programa la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La forma en que efectúe el cuerpo la ejecución depende de si <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pasa a estado inactivo.

 Si la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> no pasa a estado inactivo, se ejecuta en orden inverso porque las actividades programadas se administran como una pila, la última actividad programada se ejecuta primero. Por ejemplo, si tiene una colección de {1,2,3,4} en <xref:System.Activities.Statements.ParallelForEach%601> y usa **WriteLine** como cuerpo para escribir el valor. Tiene 4, 3, 2, 1 impresos en la consola. Esto se debe a que **WriteLine** no entra en estado inactivo, por lo que después de que se hayan programado 4 actividades **WriteLine** , se ejecutan mediante un comportamiento de pila (primero en salir).

 Pero si tiene actividades en la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> que pueden pasar a estado inactivo, como una actividad <xref:System.ServiceModel.Activities.Receive> o <xref:System.Activities.Statements.Delay>, A continuación no hay necesidad de esperarlos para completarse. <xref:System.Activities.Statements.ParallelForEach%601> va a la siguiente actividad de cuerpo programada e intenta ejecutarla. Si esa actividad también pasa a estado inactivo, <xref:System.Activities.Statements.ParallelForEach%601> vuelve a desplazarse hasta la siguiente actividad del cuerpo.

### <a name="using-the-parallelforeacht-activity-designer"></a>Usar el \<T> Diseñador de actividades ParallelForEach
 El diseñador de actividades **ParallelForEach \<T> ** se puede encontrar en la categoría **flujo de control** del cuadro de **herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** a la izquierda de [!INCLUDE[wfd2](../includes/wfd2-md.md)] . (de forma alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **ParallelForEach \<T> ** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)] , donde se coloquen normalmente los diseñadores de actividad, por ejemplo, dentro de un diseñador de actividad **Sequence** . Después de colocarlo en [!INCLUDE[wfd2](../includes/wfd2-md.md)] , crea una <xref:System.Activities.Statements.ParallelForEach%601> actividad, que de forma predeterminada contiene un <xref:System.Activities.Activity.DisplayName%2A> de **ParallelForEach \<Int32> .**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>\<T>Propiedades de ParallelForEach en el diseñador de flujo de trabajo
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.ParallelForEach%601> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica el nombre para mostrar descriptivo del diseñador de actividades en el encabezado. El valor predeterminado es **ParallelForEach \<Int32> **. El valor se puede editar opcionalmente en la cuadrícula de **propiedades** o directamente en el encabezado del diseñador de actividad.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|Falso|La actividad que se va a ejecutar para cada elemento en la colección. Para agregar la <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> actividad, coloque una actividad del cuadro de herramientas en el cuadro **Body** del diseñador de actividades ** \<T> ParallelForEach** con el texto de la sugerencia "Coloque la actividad aquí".|
|**TypeArgument**|Verdadero|Tipo de los elementos de la <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> colección especificada por el parámetro genérico *T*. De forma predeterminada, **TypeArgument** se establece en **Int32**. Para cambiar el tipo T en el diseñador de actividades **ParallelForEach \<T> ** , cambie el valor del cuadro combinado **TypeArgument** en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Verdadero|La colección de elementos en la que se va a iterar. Para establecer la propiedad <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> , escriba una [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expresión en el cuadro **valores** del diseñador de actividades **foreach \<T> ** en el cuadro con el texto de la sugerencia "Escriba una expresión de VB" o en el cuadro **valores** de la ventana **propiedades** .|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Se evalúa cuando se completa cada iteración. Si se evalúa como true, se cancelan las operaciones programadas pendientes. Si no se establece esta propiedad, se ejecutan todas las instrucciones programadas hasta su compleción.|

 De forma predeterminada, el iterador del bucle se denomina elemento. Puede cambiar el nombre de la variable de iterador en el cuadro **foreach** del diseñador de actividades **ParallelForEach \<T> ** . El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Consulte también
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md) [paralelo](../workflow-designer/parallel-activity-designer.md) de [secuencia](../workflow-designer/sequence-activity-designer.md)