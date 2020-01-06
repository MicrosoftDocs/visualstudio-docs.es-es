---
title: Diseñador de flujo de trabajo-ForEach&lt;T&gt; diseñador de actividades
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30d43351211a6ff857630b47f05be77e27bd7951
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593920"
---
# <a name="foreachlttgt-activity-designer"></a>Diseñador de actividad ForEach&lt;T&gt;

La actividad <xref:System.Activities.Statements.ForEach%601> ejecuta la actividad que se incluye en su propiedad <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada elemento en una colección <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.

## <a name="foreacht-properties-in-the-workflow-designer"></a>\> las propiedades de ForEach < T en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.ForEach%601> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Requerido|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.ForEach%601>. El valor predeterminado es ForEach < Int32\>. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Verdadero|La colección de elementos en la que se va a iterar. Para establecer el <xref:System.Activities.Statements.ForEach%601.Values%2A>, escriba una expresión de Visual Basic en el cuadro **valores** del diseñador de actividad **ForEach < t\>** o en la cuadrícula de propiedades.|
|*TypeArgument*|Verdadero|Tipo de los elementos de la colección de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificados por el parámetro genérico *t*. De forma predeterminada, *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor del cuadro combinado *TypeArgument* en la cuadrícula de propiedades.|

De forma predeterminada, el iterador del bucle se denomina **Item**. Puede cambiar el nombre de la variable de iterador en el diseñador de actividades <xref:System.Activities.Statements.ForEach%601>. El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Vea también

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
