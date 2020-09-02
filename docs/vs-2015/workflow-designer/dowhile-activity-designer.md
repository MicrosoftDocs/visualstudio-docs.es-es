---
title: Diseñador de actividad en | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656767"
---
# <a name="dowhile-activity-designer"></a>Diseñador de actividades DoWhile
La <xref:System.Activities.Statements.DoWhile> actividad ejecuta la actividad contenida en <xref:System.Activities.Statements.DoWhile.Body%2A> al menos una vez, hasta que una condición especificada se evalúa como **false**. Si necesita que se ejecute la actividad que se encuentra en un cuerpo del bucle entre cero y varias veces, utilice la actividad <xref:System.Activities.Statements.While> en su lugar.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propiedades DoWhile en el Diseñador de flujo de trabajo
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.DoWhile> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Falso|La actividad que se va a ejecutar mientras se **cumple**la condición. Para agregar la <xref:System.Activities.Statements.DoWhile.Body%2A> actividad, coloque una actividad del cuadro de herramientas en el cuadro **Body** del **DoWhile** diseñador de actividades de la actividad con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Verdadero|La condición que se va a evaluar tras cada una de las iteraciones del bucle. Para establecer la <xref:System.Activities.Statements.DoWhile.Condition%2A> propiedad, escriba una [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expresión en el cuadro **condición** en **DoWhile** el diseñador de actividades, o en la cuadrícula de propiedades.|

## <a name="see-also"></a>Consulte también
 [While](../workflow-designer/while-activity-designer.md) [Flujo de control](../workflow-designer/control-flow-activity-designers.md)