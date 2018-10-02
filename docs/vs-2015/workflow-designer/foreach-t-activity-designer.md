---
title: ForEach&lt;T&gt; Diseñador de actividad | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b118eb62f3055486e26f9d90a4e3abb74fe38660
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577375"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; Diseñador de actividad
La actividad <xref:System.Activities.Statements.ForEach%601> ejecuta la actividad que se incluye en su propiedad <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada elemento en una colección <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach\<T > Propiedades en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.ForEach%601> más útiles y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.ForEach%601>. El valor predeterminado es ForEach\<Int32 >. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|La colección de elementos en la que se va a iterar. Para establecer el <xref:System.Activities.Statements.ForEach%601.Values%2A>, escriba un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expresión en el **valores** cuadro en el **ForEach\<T >** actividad diseñador o en la cuadrícula de propiedades.|  
|*TypeArgument*|True|El tipo de los elementos de la <xref:System.Activities.Statements.ForEach%601.Values%2A> colección especificada por el parámetro genérico *T*. De forma predeterminada, *TypeArgument* está establecido en **Int32**. Para cambiar el tipo, cambie el valor de la *TypeArgument* cuadro combinado en la cuadrícula de propiedades.|  
  
 De forma predeterminada, el iterador del bucle se denomina **elemento**. Puede cambiar el nombre de la variable de iterador en el diseñador de actividades <xref:System.Activities.Statements.ForEach%601>. El iterador del bucle se puede utilizar en expresiones en los elementos secundarios de la actividad <xref:System.Activities.Statements.ForEach%601>.  
  
## <a name="see-also"></a>Vea también  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)