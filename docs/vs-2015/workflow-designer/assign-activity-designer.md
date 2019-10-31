---
title: Diseñador de actividad Assign | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ebe465d5eeb12a956d285a8313b0acdbcfb8d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659185"
---
# <a name="assign-activity-designer"></a>Diseñador de actividades Assign
El diseñador de actividades **assign** se usa para crear y configurar una actividad <xref:System.Activities.Statements.Assign>.

## <a name="the-assign-activity"></a>Actividad Assign
 La actividad <xref:System.Activities.Statements.Assign> asigna un valor a una variable o argumento.

### <a name="using-the-assign-activity-designer"></a>Utilizar el diseñador de actividades Assign
 El diseñador de actividades **assign** se puede encontrar en la categoría **primitivas** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** . (de forma alternativa, seleccione **cuadro de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **assign** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)] donde se colocan normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.Assign> con un valor **displayName** predeterminado de Assign. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **assign** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-assign-properties"></a>Propiedades Assign
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Assign> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.Assign>. El valor predeterminado es Assign. Pese a que el valor <xref:System.Activities.Activity.DisplayName%2A> no es obligatorio, se recomienda usar uno.|
|<xref:System.Activities.Statements.Assign.To%2A>|True|La variable o argumento al que está asignado <xref:System.Activities.Statements.Assign.Value%2A>. Debe ser un identificador de Visual Basic válido. Para establecer la propiedad, escriba una expresión de Visual Basic en el cuadro **para** del diseñador de actividades **assign** o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valor que se asigna a la variable. Para establecer el <xref:System.Activities.Statements.Assign.Value%2A>, escriba una expresión de Visual Basic en el cuadro **valor** del diseñador de actividades **assign** o en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también
 [Primitivos](../workflow-designer/primitives-activity-designers.md) [Retraso](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)