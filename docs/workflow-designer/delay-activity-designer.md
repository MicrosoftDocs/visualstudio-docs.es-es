---
title: Retrasar el Diseñador de actividades | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7159330588151d4845184fcb6688b20f8d13afd0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="delay-activity-designer"></a>Diseñador de actividades Delay
El **retraso** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.Delay> actividad.

## <a name="the-delay-activity"></a>Actividad Delay
 La actividad <xref:System.Activities.Statements.Delay> retrasa la ejecución de un flujo de trabajo durante un periodo de tiempo determinado.

### <a name="using-the-delay-activity-designer"></a>Utilizar el diseñador de actividades Delay
 El **retraso** Diseñador de actividad puede encontrarse en el **primitivas** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**pestaña de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (o bien, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

 El **retraso** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] expuesta, donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.Delay> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Delay. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **retraso** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-delay-properties"></a>Propiedades Delay
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Delay> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Delay>. El valor predeterminado es Delay. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Tiempo durante el que se va a retrasar el flujo de trabajo. Esta propiedad se establece en la cuadrícula de propiedades. Escriba un <xref:System.TimeSpan> literal con formato 00:00:00 o una expresión de Visual Basic para especificar la duración.|

## <a name="see-also"></a>Vea también

- [Elementos primitivos](../workflow-designer/primitives-activity-designers.md)
- [asignar](../workflow-designer/assign-activity-designer.md)
- [Diseñador de actividad Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)