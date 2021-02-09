---
title: 'Diseñador de flujo de trabajo: diseñador de actividad Delay'
description: Obtenga información sobre las actividades de retraso y cómo puede usar el diseñador de actividad Delay para crear y configurar una actividad Delay.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b661dddf6c07bca34e5ea044fd1338da68f4e19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894314"
---
# <a name="delay-activity-designer"></a>Diseñador de actividades Delay

El diseñador de actividad **Delay** se usa para crear y configurar una <xref:System.Activities.Statements.Delay> actividad.

## <a name="the-delay-activity"></a>Actividad Delay

La actividad <xref:System.Activities.Statements.Delay> retrasa la ejecución de un flujo de trabajo durante un periodo de tiempo determinado.

### <a name="use-the-delay-activity-designer"></a>Usar el diseñador de actividad Delay

El diseñador de actividades **Delay** se puede encontrar en la categoría **primitivas** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** del diseñador de flujo de trabajo. Como alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o presione **Ctrl** + **Alt** + **X**.

El diseñador de actividades **Delay** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde normalmente se colocan las actividades, como en una <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividad, se crea una <xref:System.Activities.Statements.Delay> actividad con un valor predeterminado <xref:System.Activities.Activity.DisplayName%2A> de delay. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividad **Delay** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-delay-properties"></a>Propiedades de retraso

En la tabla siguiente se muestran las <xref:System.Activities.Statements.Delay> propiedades y se describe cómo se usan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas se pueden editar en la superficie Diseñador de flujo de trabajo.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Delay>. El valor predeterminado es Delay. Aunque el <xref:System.Activities.Activity.DisplayName%2A> valor no es estrictamente necesario, se recomienda usar uno.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Tiempo durante el que se va a retrasar el flujo de trabajo. Esta propiedad se establece en la cuadrícula de propiedades. Escriba un <xref:System.TimeSpan> literal con formato 00:00:00 o una expresión de Visual Basic para especificar la duración.|

## <a name="see-also"></a>Vea también

- [Elementos primitivos](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Diseñador de actividades Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)