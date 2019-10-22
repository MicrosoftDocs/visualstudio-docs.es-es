---
title: Diseñador de flujo de trabajo-ForEach &lt;T diseñador de actividad &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faf2f62c482deac963f597c9861fbf2acedc945c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650396"
---
# <a name="foreachlttgt-activity-designer"></a>Diseñador de actividades &gt; de &lt;T ForEach

La actividad <xref:System.Activities.Statements.ForEach%601> ejecuta la actividad que se incluye en su propiedad <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada elemento en una colección <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.

## <a name="foreacht-properties-in-the-workflow-designer"></a>@No__t_0 las propiedades de ForEach < T en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.ForEach%601> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.ForEach%601>. El valor predeterminado es ForEach < Int32 \>. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|La colección de elementos en la que se va a iterar. Para establecer el <xref:System.Activities.Statements.ForEach%601.Values%2A>, escriba una expresión de Visual Basic en el cuadro **valores** del diseñador de actividad **ForEach < t \>** o en la cuadrícula de propiedades.|
|*TypeArgument*|True|Tipo de los elementos de la colección de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificados por el parámetro genérico *t*. De forma predeterminada, *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor del cuadro combinado *TypeArgument* en la cuadrícula de propiedades.|

De forma predeterminada, el iterador del bucle se denomina **Item**. Puede cambiar el nombre de la variable de iterador en el diseñador de actividades <xref:System.Activities.Statements.ForEach%601>. El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Vea también

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)