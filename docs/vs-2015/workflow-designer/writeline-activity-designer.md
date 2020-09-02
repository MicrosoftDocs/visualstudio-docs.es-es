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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657532"
---
# <a name="writeline-activity-designer"></a>Diseñador de actividades WriteLine
El diseñador de actividades **WriteLine** se usa para crear y configurar una <xref:System.Activities.Statements.WriteLine> actividad.

## <a name="the-writeline-activity"></a>Actividad WriteLine
 La actividad <xref:System.Activities.Statements.WriteLine> escribe texto en un objeto <xref:System.IO.TextWriter> especificado. Si no se especifica un objeto <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> escribe el texto en la consola.

### <a name="using-the-writeline-activity-designer"></a>Utilizar el diseñador de actividades WriteLine
 El diseñador de actividades **WriteLine** se puede encontrar en la categoría **primitivas** del **cuadro de herramientas**, al que se tiene acceso al hacer clic en la pestaña **cuadro de herramientas** de. (de forma [!INCLUDE[wfd2](../includes/wfd2-md.md)] alternativa, seleccione **barra de herramientas** en el menú **Ver** o Ctrl + Alt + X).

 El diseñador de actividades **WriteLine** se puede arrastrar desde el **cuadro de herramientas** y colocarlo en la [!INCLUDE[wfd2](../includes/wfd2-md.md)] superficie de, donde se coloquen normalmente las actividades, como en una <xref:System.Activities.Statements.Sequence> . Esto crea una actividad <xref:System.Activities.Statements.WriteLine> con una propiedad <xref:System.Activities.Activity.DisplayName%2A> predeterminada de WriteLine. <xref:System.Activities.Activity.DisplayName%2A>Se puede editar en el encabezado del diseñador de actividades **WriteLine** o en el cuadro **displayName** de la cuadrícula de propiedades.

### <a name="the-writeline-properties"></a>Propiedades WriteLine
 En la tabla siguiente se muestran las propiedades <xref:System.Activities.Statements.WriteLine> y se describe cómo se utilizan en el diseñador. Estas propiedades se pueden editar en una cuadrícula de propiedades y algunas de ellas en la superficie del diseñador [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Nombre descriptivo de la actividad <xref:System.Activities.Statements.WriteLine>. El valor predeterminado es WriteLine. Pese a que la propiedad <xref:System.Activities.Activity.DisplayName%2A> no es obligatoria, se recomienda utilizar una.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Falso|Texto que se va a escribir. Para establecer la propiedad, escriba una expresión de Visual Basic en el cuadro de **texto** del diseñador de actividades **WriteLine** o en la cuadrícula de propiedades.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Falso|El objeto <xref:System.IO.TextWriter> en el que <xref:System.Activities.Statements.WriteLine> escribe la propiedad <xref:System.Activities.Statements.WriteLine.Text%2A>. El valor predeterminado es la consola.|

## <a name="see-also"></a>Consulte también
 Intervalos de [tiempo de espera](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) de [asignación](../workflow-designer/assign-activity-designer.md) de [primitivos](../workflow-designer/primitives-activity-designers.md)