---
title: Diseñador de actividades WriteLine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4f656578526879774e698523239d5a9b2b14ccd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657532"
---
# <a name="writeline-activity-designer"></a>Diseñador de actividades WriteLine
El diseñador de actividades **WriteLine** se usa para crear y configurar una actividad <xref:System.Activities.Statements.WriteLine>.

## <a name="the-writeline-activity"></a>Actividad WriteLine
 La actividad <xref:System.Activities.Statements.WriteLine> escribe texto en un objeto <xref:System.IO.TextWriter> especificado. Si no se especifica un objeto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> escribe el texto en la consola.

### <a name="using-the-writeline-activity-designer"></a>Utilizar el diseñador de actividades WriteLine
 El diseñador de actividades **WriteLine** se puede encontrar en la categoría **primitivas** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** del [!INCLUDE[wfd2](../includes/wfd2-md.md)] (de forma alternativa, seleccione barra de **herramientas** en el menú **Ver** o CTRL + ALT + X).

 El diseñador de actividades **WriteLine** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la superficie de [!INCLUDE[wfd2](../includes/wfd2-md.md)] siempre que se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence>. Esto crea una actividad <xref:System.Activities.Statements.WriteLine> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de WriteLine. El <xref:System.Activities.Activity.DisplayName%2A> se puede editar en el encabezado del diseñador de actividades **WriteLine** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-writeline-properties"></a>Propiedades WriteLine
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.WriteLine> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nombre descriptivo de la actividad <xref:System.Activities.Statements.WriteLine>. El valor predeterminado es WriteLine. Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Texto que se va a escribir. Para establecer la propiedad, escriba una expresión de Visual Basic en el cuadro de **texto** del diseñador de actividades **WriteLine** o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|El objeto <xref:System.IO.TextWriter> en el que <xref:System.Activities.Statements.WriteLine> escribe la propiedad <xref:System.Activities.Statements.WriteLine.Text%2A>. El valor predeterminado es la consola.|

## <a name="see-also"></a>Vea también
 [Primitivos](../workflow-designer/primitives-activity-designers.md) [Asignación](../workflow-designer/assign-activity-designer.md) [Retraso](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)