---
title: Diseñador de actividad Diseñador de flujo de trabajo-while
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6570a80de5be17b2893fc4105f057e655e841881
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649765"
---
# <a name="while-activity-designer"></a>Diseñador de actividades While

La actividad <xref:System.Activities.Statements.While> ejecuta la actividad contenida en su <xref:System.Activities.Statements.While.Body%2A> mientras el <xref:System.Activities.Statements.While.Condition%2A> especificado se evalúa como **true**. La actividad contenida nunca se puede ejecutar. Si desea ejecutar la actividad contenida al menos una vez, utilice la actividad <xref:System.Activities.Statements.DoWhile> en su lugar.

## <a name="while-properties-in-workflow-designer"></a>Propiedades While en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.While> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Requerido|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.While> en el encabezado. El valor predeterminado es While. El valor se puede editar en la ventana **propiedades** o directamente en el encabezado del diseñador de actividad.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Contiene la actividad que se va a ejecutar mientras el <xref:System.Activities.Statements.While.Condition%2A> se evalúa como **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contiene la expresión Visual Basic que se evalúa para determinar si se va a ejecutar la actividad en el <xref:System.Activities.Statements.While.Body%2A>.|

## <a name="see-also"></a>Vea también

- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)