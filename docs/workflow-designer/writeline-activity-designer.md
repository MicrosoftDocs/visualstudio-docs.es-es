---
title: Diseñador de flujo de trabajo - Diseñador de actividades WriteLine
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b77ab2b9effc305469b3a4e489342f496a89997
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755955"
---
# <a name="writeline-activity-designer"></a>Diseñador de actividades WriteLine

El **WriteLine** Diseñador de actividad se usa para crear y configurar un <xref:System.Activities.Statements.WriteLine> actividad.

## <a name="the-writeline-activity"></a>Actividad WriteLine

La actividad <xref:System.Activities.Statements.WriteLine> escribe texto en un objeto <xref:System.IO.TextWriter> especificado. Si no se especifica un objeto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> escribe el texto en la consola.

### <a name="using-the-writeline-activity-designer"></a>Utilizar el diseñador de actividades WriteLine

Acceso a la **WriteLine** Diseñador de actividad en el **primitivas** categoría de la **cuadro de herramientas**. El **WriteLine** Diseñador de actividad se puede arrastrar desde el **cuadro de herramientas** y colocar en la superficie del Diseñador de flujo de trabajo donde se coloquen normalmente las actividades, tal como en un <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.WriteLine> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de WriteLine. El <xref:System.Activities.Activity.DisplayName%2A> se pueden editar en el encabezado de la **WriteLine** Diseñador de actividad o en el **DisplayName** cuadro de la cuadrícula de propiedades.

### <a name="the-writeline-properties"></a>Propiedades WriteLine

En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.WriteLine> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en cuadrícula de propiedades y algunas de ellas se pueden editar en la superficie del Diseñador de flujo de trabajo.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.WriteLine>. El valor predeterminado es WriteLine. Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Texto que se va a escribir. Para establecer la propiedad, escriba una expresión de Visual Basic en el **texto** cuadro en el **WriteLine** actividad diseñador o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|El objeto <xref:System.IO.TextWriter> en el que <xref:System.Activities.Statements.WriteLine> escribe la propiedad <xref:System.Activities.Statements.WriteLine.Text%2A>. El valor predeterminado es la consola.|

## <a name="see-also"></a>Vea también

- [Elementos primitivos](../workflow-designer/primitives-activity-designers.md)
- [Asignar](../workflow-designer/assign-activity-designer.md)
- [Retraso](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)