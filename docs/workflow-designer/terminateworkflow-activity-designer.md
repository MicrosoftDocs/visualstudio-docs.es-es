---
title: Diseñador de actividades TerminateWorkflow | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 444ea597fd6c76c8312369afcbc497e640bace6f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="terminateworkflow-activity-designer"></a>Diseñador actividades TerminateWorkflow
El **TerminateWorkflow** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.TerminateWorkflow> actividad.

## <a name="the-terminateworkflow-activity"></a>Actividad TerminateWorkflow
 La actividad <xref:System.Activities.Statements.TerminateWorkflow> finaliza la ejecución de un flujo de trabajo.

### <a name="using-the-terminateworkflow-activity-designer"></a>Utilizar el diseñador de actividades TerminateWorkflow
 El **TerminateWorkflow** Diseñador de actividad puede encontrarse en el **en tiempo de ejecución** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas** pestaña (o bien, seleccione **cuadro de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **TerminateWorkflow** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Esto crea una <xref:System.Activities.Statements.TerminateWorkflow> actividad con el valor predeterminado es **DisplayName** de TerminateWorkflow. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **TerminateWorkflow** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-terminateworkflow-properties"></a>Propiedades TerminateWorkflow
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.TerminateWorkflow> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.TerminateWorkflow>. El valor predeterminado es TerminateWorkflow. Aunque el nombre para mostrar no es obligatorio, se recomienda utilizarlo.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|La excepción que se va a producir cuando se finaliza el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|La razón que explica por qué finalizó el flujo de trabajo. Establezca esta propiedad en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [Tiempo de ejecución](../workflow-designer/runtime-activity-designers.md)
- [Conservar](../workflow-designer/persist-activity-designer.md)