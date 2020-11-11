---
title: 'Diseñador de flujo de trabajo: asignar el diseñador de actividades'
description: Obtenga información sobre cómo puede utilizar el diseñador de actividades Assign para crear y configurar una actividad Assign y cómo la actividad Assign asigna un valor a una variable o argumento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d8601951cfaba3f246e8488ab23c9b6ccad0d01
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438196"
---
# <a name="assign-activity-designer"></a>Diseñador de actividades Assign

El diseñador de actividades **assign** se usa para crear y configurar una <xref:System.Activities.Statements.Assign> actividad.

## <a name="the-assign-activity"></a>Actividad Assign

La actividad <xref:System.Activities.Statements.Assign> asigna un valor a una variable o argumento.

### <a name="using-the-assign-activity-designer"></a>Utilizar el diseñador de actividades Assign

El diseñador de actividades **assign** se puede encontrar en la categoría **primitivas** del **cuadro de herramientas** , al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** . (de forma alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o Ctrl + Alt + X).

El diseñador de actividades **assign** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo en la que se colocan las actividades, como en una <xref:System.Activities.Statements.Sequence> . Al quitar el diseñador de actividades **assign** , se crea una <xref:System.Activities.Statements.Assign> actividad con un valor **displayName** predeterminado de Assign. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **assign** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-assign-properties"></a>Propiedades Assign

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Assign> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas se pueden editar en Diseñador de flujo de trabajo superficie.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Assign>. El valor predeterminado es Assign. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|La variable o argumento al que está asignado <xref:System.Activities.Statements.Assign.Value%2A>. El valor debe ser un identificador de Visual Basic válido. Para establecer la propiedad, escriba una expresión de Visual Basic en el cuadro **para** del diseñador de actividades **assign** o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valor que se asigna a la variable. Para establecer <xref:System.Activities.Statements.Assign.Value%2A> , escriba una expresión de Visual Basic en el cuadro **valor** en el diseñador de actividades **assign** o en la cuadrícula de propiedades.|

## <a name="see-also"></a>Consulte también

- [Elementos primitivos](../workflow-designer/primitives-activity-designers.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)