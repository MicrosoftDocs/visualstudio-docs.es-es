---
title: Diseñador de flujo de trabajo - Diseñador de actividades DoWhile
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19817fb23bd8a22532df7d349262b689f632a3a7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839627"
---
# <a name="dowhile-activity-designer"></a>Diseñador de actividades DoWhile

El <xref:System.Activities.Statements.DoWhile> actividad ejecuta la actividad contenida en su <xref:System.Activities.Statements.DoWhile.Body%2A> al menos una vez, hasta que una condición especificada se evalúa como **false**. Si necesita que se ejecute la actividad que se encuentra en un cuerpo del bucle entre cero y varias veces, utilice la actividad <xref:System.Activities.Statements.While> en su lugar.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propiedades DoWhile en el Diseñador de flujo de trabajo

La tabla siguiente muestran los más útiles <xref:System.Activities.Statements.DoWhile> propiedades de la actividad y se describe cómo se usan en el diseñador:

|Nombre de la propiedad|Obligatorio|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|La actividad para ejecutar mientras la condición es **true**. Para agregar la <xref:System.Activities.Statements.DoWhile.Body%2A> actividad, coloque una actividad en el cuadro de herramientas en el **cuerpo** cuadro en el **DoWhile** Diseñador de actividad con el texto de la sugerencia "Coloque la actividad aquí".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|La condición que se va a evaluar tras cada una de las iteraciones del bucle. Para establecer el <xref:System.Activities.Statements.DoWhile.Condition%2A>, escriba una expresión de Visual Basic en el **condición** cuadro en el **DoWhile** actividad diseñador o en la cuadrícula de propiedades.|

## <a name="see-also"></a>Vea también

- [While](../workflow-designer/while-activity-designer.md)
- [Flujo de control](../workflow-designer/control-flow-activity-designers.md)