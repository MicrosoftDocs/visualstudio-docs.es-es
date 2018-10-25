---
title: Diseñador de flujo de trabajo - Diseñador de actividad TerminateWorkflow
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f11cbf6ac5a0b19022794aaafd59afe96f51273b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908059"
---
# <a name="terminateworkflow-activity-designer"></a>Diseñador actividades TerminateWorkflow

El **TerminateWorkflow** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.TerminateWorkflow> actividad.

## <a name="the-terminateworkflow-activity"></a>Actividad TerminateWorkflow

La actividad <xref:System.Activities.Statements.TerminateWorkflow> finaliza la ejecución de un flujo de trabajo.

### <a name="using-the-terminateworkflow-activity-designer"></a>Utilizar el diseñador de actividades TerminateWorkflow

El **TerminateWorkflow** Diseñador de actividad puede encontrarse en el **en tiempo de ejecución** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas** ficha (como alternativa, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)

El **TerminateWorkflow** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea un <xref:System.Activities.Statements.TerminateWorkflow> actividad con un valor predeterminado **DisplayName** de TerminateWorkflow. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **TerminateWorkflow** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-terminateworkflow-properties"></a>Propiedades TerminateWorkflow

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TerminateWorkflow> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades y algunas de ellas se pueden editar en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.TerminateWorkflow>. El valor predeterminado es TerminateWorkflow. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|La excepción que se va a producir cuando se finaliza el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|La razón que explica por qué finalizó el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)