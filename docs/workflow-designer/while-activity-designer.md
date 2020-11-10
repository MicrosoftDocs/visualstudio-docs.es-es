---
title: Diseñador de actividad Diseñador de flujo de trabajo-while
description: Obtenga información sobre cómo la actividad while ejecuta la actividad contenida en su cuerpo mientras la condición especificada se evalúa como true.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2e78d4f2e6aa332c9dfd5faebf834e4f5015c454
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433705"
---
# <a name="while-activity-designer"></a>Diseñador de actividades While

La <xref:System.Activities.Statements.While> actividad ejecuta la actividad contenida en su <xref:System.Activities.Statements.While.Body%2A> mientras el especificado <xref:System.Activities.Statements.While.Condition%2A> se evalúa como **true**. La actividad contenida nunca se puede ejecutar. Si desea ejecutar la actividad contenida al menos una vez, utilice la actividad <xref:System.Activities.Statements.DoWhile> en su lugar.

## <a name="while-properties-in-workflow-designer"></a>Propiedades While en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.While> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica el nombre descriptivo del diseñador de actividades <xref:System.Activities.Statements.While> en el encabezado. El valor predeterminado es While. El valor se puede editar en la ventana **propiedades** o directamente en el encabezado del diseñador de actividad.<br /><br /> Aunque el valor de la propiedad <xref:System.Activities.Activity.DisplayName%2A> no sea obligatorio, el procedimiento recomendado es usar uno.|
|<xref:System.Activities.Statements.While.Body%2A>|Falso|Contiene la actividad que se va a ejecutar mientras que se <xref:System.Activities.Statements.While.Condition%2A> evalúa como **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contiene la expresión Visual Basic que se evalúa para determinar si se va a ejecutar la actividad en <xref:System.Activities.Statements.While.Body%2A> .|

## <a name="see-also"></a>Consulte también

- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
