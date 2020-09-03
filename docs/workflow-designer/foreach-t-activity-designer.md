---
title: Diseñador de flujo de trabajo- &lt; Diseñador de &gt; actividades foreach T
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593920"
---
# <a name="foreachlttgt-activity-designer"></a>&lt;Diseñador de &gt; actividades foreach T

La actividad <xref:System.Activities.Statements.ForEach%601> ejecuta la actividad que se incluye en su propiedad <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada elemento en una colección <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Propiedades ForEach<T \> en el diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.ForEach%601> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.ForEach%601>. El valor predeterminado es ForEach<Int32 \> . Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Verdadero|La colección de elementos en la que se va a iterar. Para establecer <xref:System.Activities.Statements.ForEach%601.Values%2A> , escriba una expresión de Visual Basic en el cuadro **valores** del diseñador de actividades **foreach \><T** o en la cuadrícula de propiedades.|
|*TypeArgument*|Verdadero|Tipo de los elementos de la <xref:System.Activities.Statements.ForEach%601.Values%2A> colección especificada por el parámetro genérico *T*. De forma predeterminada, *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor del cuadro combinado *TypeArgument* en la cuadrícula de propiedades.|

De forma predeterminada, el iterador del bucle se denomina **Item**. Puede cambiar el nombre de la variable de iterador en el diseñador de actividades <xref:System.Activities.Statements.ForEach%601>. El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Vea también

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
