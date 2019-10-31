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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656767"
---
# <a name="dowhile-activity-designer"></a>Diseñador de actividades DoWhile
La actividad <xref:System.Activities.Statements.DoWhile> ejecuta la actividad contenida en su <xref:System.Activities.Statements.DoWhile.Body%2A> al menos una vez, hasta que una condición especificada se evalúa como **false**. Si necesita que se ejecute la actividad que se encuentra en un cuerpo del bucle entre cero y varias veces, utilice la actividad <xref:System.Activities.Statements.While> en su lugar.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propiedades DoWhile en el Diseñador de flujo de trabajo
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.DoWhile> más útiles y se describe cómo se utilizan en el diseñador.

|Nombre de la propiedad|Obligatorio|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|La actividad que se va a ejecutar mientras se **cumple**la condición. Para agregar la actividad <xref:System.Activities.Statements.DoWhile.Body%2A>, coloque una actividad del cuadro de herramientas en el cuadro **Body** del **Diseñador de actividades de** la actividad, con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|La condición que se va a evaluar tras cada una de las iteraciones del bucle. Para establecer el <xref:System.Activities.Statements.DoWhile.Condition%2A>, escriba una expresión de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] en el cuadro **condición** en el diseñador **de actividades,** o en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md) [While](../workflow-designer/while-activity-designer.md)