---
title: Diseñador de actividad &gt; de &lt;T ForEach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d41451ada0e37f953e9d611a4e3733815a9d347b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656651"
---
# <a name="foreachlttgt-activity-designer"></a>Diseñador de actividades &gt; de &lt;T ForEach
La actividad <xref:System.Activities.Statements.ForEach%601> ejecuta la actividad que se incluye en su propiedad <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada elemento en una colección <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.

## <a name="foreacht-properties-in-the-workflow-designer"></a>@No__t_0T ForEach > Propiedades en el Diseñador de flujo de trabajo
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.ForEach%601> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.ForEach%601>. El valor predeterminado es ForEach \<Int32 >. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|La colección de elementos en la que se va a iterar. Para establecer el <xref:System.Activities.Statements.ForEach%601.Values%2A>, escriba una expresión de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] en el cuadro **valores** del diseñador de actividad **foreach \<T >** o en la cuadrícula de propiedades.|
|*TypeArgument*|True|Tipo de los elementos de la colección de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificados por el parámetro genérico *t*. De forma predeterminada, *TypeArgument* se establece en **Int32**. Para cambiar el tipo, cambie el valor del cuadro combinado *TypeArgument* en la cuadrícula de propiedades.|

 De forma predeterminada, el iterador del bucle se denomina **Item**. Puede cambiar el nombre de la variable de iterador en el diseñador de actividades <xref:System.Activities.Statements.ForEach%601>. El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ForEach%601>.

## <a name="see-also"></a>Vea también
 [ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md) [flujo de control](../workflow-designer/control-flow-activity-designers.md)