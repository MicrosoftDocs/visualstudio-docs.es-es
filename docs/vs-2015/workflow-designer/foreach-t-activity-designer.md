---
title: ForEach&lt;T&gt; Diseñador de actividad | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 97732b92c5a90334917ad4e74667f88d605b647d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943296"
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
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)