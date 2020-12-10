---
title: Diseñador de actividades TerminateWorkflow
description: En Diseñador de flujo de trabajo, obtenga información sobre cómo puede utilizar el diseñador de actividades TerminateWorkflow para crear y configurar una actividad TerminateWorkflow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fc52153ca71320ebe2ebc1e1a12780e37cac08e
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995456"
---
# <a name="terminateworkflow-activity-designer"></a>Diseñador actividades TerminateWorkflow

El diseñador de actividades **TerminateWorkflow** se utiliza para crear y configurar una <xref:System.Activities.Statements.TerminateWorkflow> actividad.

## <a name="the-terminateworkflow-activity"></a>Actividad TerminateWorkflow

La actividad <xref:System.Activities.Statements.TerminateWorkflow> finaliza la ejecución de un flujo de trabajo.

### <a name="using-the-terminateworkflow-activity-designer"></a>Utilizar el diseñador de actividades TerminateWorkflow

El diseñador de actividades **TerminateWorkflow** se puede encontrar en la categoría **tiempo de ejecución** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña cuadro de **herramientas** . (de forma alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o Ctrl + Alt + X).

El diseñador de actividades **TerminateWorkflow** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie diseñador de flujo de trabajo, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una <xref:System.Activities.Statements.TerminateWorkflow> actividad con un valor **displayName** predeterminado de TerminateWorkflow. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **TerminateWorkflow** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-terminateworkflow-properties"></a>Propiedades TerminateWorkflow

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TerminateWorkflow> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas se pueden editar en Diseñador de flujo de trabajo superficie.

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.TerminateWorkflow>. El valor predeterminado es TerminateWorkflow. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Falso|La excepción que se va a producir cuando se finaliza el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Falso|La razón que explica por qué finalizó el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|

## <a name="see-also"></a>Consulte también

- [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)
