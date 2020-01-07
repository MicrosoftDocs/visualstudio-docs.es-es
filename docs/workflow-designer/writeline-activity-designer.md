---
title: Diseñador de actividades Diseñador de flujo de trabajo-WriteLine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e3b4da69a2d9154f36e42d3b20657e204767872
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593029"
---
# <a name="writeline-activity-designer"></a>Diseñador de actividades WriteLine

El diseñador de actividades **WriteLine** se usa para crear y configurar una actividad <xref:System.Activities.Statements.WriteLine>.

## <a name="the-writeline-activity"></a>Actividad WriteLine

La actividad <xref:System.Activities.Statements.WriteLine> escribe texto en un objeto <xref:System.IO.TextWriter> especificado. Si no se especifica un objeto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> escribe el texto en la consola.

### <a name="using-the-writeline-activity-designer"></a>Utilizar el diseñador de actividades WriteLine

Obtenga acceso al diseñador de actividades **WriteLine** en la categoría **primitivas** del **cuadro de herramientas**. El diseñador de actividades **WriteLine** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de diseñador de flujo de trabajo siempre que se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.WriteLine> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de WriteLine. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **WriteLine** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-writeline-properties"></a>Propiedades WriteLine

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.WriteLine> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en la cuadrícula de propiedades y algunas de ellas se pueden editar en Diseñador de flujo de trabajo superficie.

|Nombre de la propiedad|Requerido|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.WriteLine>. El valor predeterminado es WriteLine. Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Falso|Texto que se va a escribir. Para establecer la propiedad, escriba una expresión de Visual Basic en el cuadro de **texto** del diseñador de actividades **WriteLine** o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Falso|El objeto <xref:System.IO.TextWriter> en el que <xref:System.Activities.Statements.WriteLine> escribe la propiedad <xref:System.Activities.Statements.WriteLine.Text%2A>. El valor predeterminado es la consola.|

## <a name="see-also"></a>Vea también

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
