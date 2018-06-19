---
title: Diseñador de flujo de trabajo - Diseñador de actividades Delay
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e22c80712bcb0c792fb929ae85b84912122a0bc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971659"
---
# <a name="delay-activity-designer"></a>Diseñador de actividades Delay

El **retraso** Diseñador de actividades se usa para crear y configurar un <xref:System.Activities.Statements.Delay> actividad.

## <a name="the-delay-activity"></a>Actividad Delay

La actividad <xref:System.Activities.Statements.Delay> retrasa la ejecución de un flujo de trabajo durante un periodo de tiempo determinado.

### <a name="using-the-delay-activity-designer"></a>Utilizar el diseñador de actividades Delay

El **retraso** Diseñador de actividad puede encontrarse en el **primitivas** categoría de la **cuadro de herramientas**, que se tiene acceso haciendo clic en el **delcuadrodeherramientas**ficha del Diseñador de flujo de trabajo (como alternativa, seleccione **barra de herramientas** desde el **vista** menú o CTRL + ALT + X.)

El **retraso** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, por ejemplo, como en un <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.Delay> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de Delay. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **retraso** Diseñador de actividad o en la **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-delay-properties"></a>Propiedades Delay

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.Delay> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades y de ellos algunas se pueden editar en la superficie de flujo de trabajo Designerdesigner.

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