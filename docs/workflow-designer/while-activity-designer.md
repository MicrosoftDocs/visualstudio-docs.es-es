---
title: Diseñador de flujo de trabajo - al diseñador de actividad
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81caba883293a59fe67988d34785758340b4705a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987042"
---
# <a name="while-activity-designer"></a>Diseñador de actividades While

El <xref:System.Activities.Statements.While> actividad ejecuta la actividad contenida en su <xref:System.Activities.Statements.While.Body%2A> mientras especificado <xref:System.Activities.Statements.While.Condition%2A> se evalúa como **true**. La actividad contenida nunca se puede ejecutar. Si desea ejecutar la actividad contenida al menos una vez, utilice la actividad <xref:System.Activities.Statements.DoWhile> en su lugar.

## <a name="while-properties-in-workflow-designer"></a>Propiedades While en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.While> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.While> en el encabezado. El valor predeterminado es While. El valor puede modificarse en el **propiedades** ventana o directamente en el encabezado del Diseñador de actividad.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Contiene la actividad para ejecutar mientras la <xref:System.Activities.Statements.While.Condition%2A> se evalúa como **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contiene la expresión de Visual Basic que se evalúa para determinar si la actividad en el <xref:System.Activities.Statements.While.Body%2A> se ejecuta.|

## <a name="see-also"></a>Vea también

- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)