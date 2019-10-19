---
title: Diseñador de actividad Delay | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656802"
---
# <a name="delay-activity-designer"></a>Diseñador de actividades Delay
El diseñador de actividad **Delay** se usa para crear y configurar una actividad <xref:System.Activities.Statements.Delay>.

## <a name="the-delay-activity"></a>Actividad Delay
 La actividad <xref:System.Activities.Statements.Delay> retrasa la ejecución de un flujo de trabajo durante un periodo de tiempo determinado.

### <a name="using-the-delay-activity-designer"></a>Utilizar el diseñador de actividades Delay
 El diseñador de actividades **Delay** se puede encontrar en la categoría **primitivas** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** del [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione barra de **herramientas** en el menú **Ver** o Ctrl + ALT + X).

 El diseñador de actividades **Delay** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie [!INCLUDE[wfd2](../includes/wfd2-md.md)], donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.Delay> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Delay. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividad **Delay** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-delay-properties"></a>Propiedades Delay
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Delay> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de la propiedad|Requerido|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Delay>. El valor predeterminado es Delay. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Tiempo durante el que se va a retrasar el flujo de trabajo. Esta propiedad se establece en la cuadrícula de propiedades. Escriba un <xref:System.TimeSpan> literal con formato 00:00:00 o una expresión de Visual Basic para especificar la duración.|

## <a name="see-also"></a>Vea también
 [Primitivas](../workflow-designer/primitives-activity-designers.md) [assign](../workflow-designer/assign-activity-designer.md) [Delay Activity Designer](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)