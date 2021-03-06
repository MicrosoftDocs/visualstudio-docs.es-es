---
title: Diseñador de flujo de trabajo-while (diseñador de actividades)
description: Obtenga información sobre cómo la actividad while ejecuta la actividad contenida en su cuerpo al menos una vez, hasta que una condición especificada se evalúe como false.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e117fcbea0488c4b6a42125971984b86cf78251
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894262"
---
# <a name="dowhile-activity-designer"></a>Diseñador de actividades DoWhile

La <xref:System.Activities.Statements.DoWhile> actividad ejecuta la actividad contenida en <xref:System.Activities.Statements.DoWhile.Body%2A> al menos una vez, hasta que una condición especificada se evalúa como **false**. Si necesita que se ejecute la actividad que se encuentra en un cuerpo del bucle entre cero y varias veces, utilice la actividad <xref:System.Activities.Statements.While> en su lugar.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propiedades DoWhile en el Diseñador de flujo de trabajo

En la tabla siguiente se muestran las <xref:System.Activities.Statements.DoWhile> propiedades de actividad más útiles y se describe cómo se usan en el diseñador:

|Nombre de propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|La actividad que se va a ejecutar mientras se **cumple** la condición. Para agregar la <xref:System.Activities.Statements.DoWhile.Body%2A> actividad, coloque una actividad del cuadro de herramientas en el cuadro **Body** del  diseñador de actividades de la actividad con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|La condición que se va a evaluar tras cada una de las iteraciones del bucle. Para establecer la <xref:System.Activities.Statements.DoWhile.Condition%2A> propiedad, escriba una expresión de Visual Basic  en el cuadro condición **del** diseñador de actividades, o en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [While](../workflow-designer/while-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)