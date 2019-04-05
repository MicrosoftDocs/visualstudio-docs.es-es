---
title: Diseñador de actividad DoWhile | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09954409baccfdc5d9eb083a15bd02f5d16cb85
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994940"
---
# <a name="dowhile-activity-designer"></a>Diseñador de actividades DoWhile
El <xref:System.Activities.Statements.DoWhile> actividad ejecuta la actividad contenida en su <xref:System.Activities.Statements.DoWhile.Body%2A> al menos una vez, hasta que una condición especificada se evalúa como **false**. Si necesita que se ejecute la actividad que se encuentra en un cuerpo del bucle entre cero y varias veces, utilice la actividad <xref:System.Activities.Statements.While> en su lugar.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>Propiedades DoWhile en el Diseñador de flujo de trabajo  
 En la tabla siguiente se muestran las actividades <xref:System.Activities.Statements.DoWhile> más útiles y se describe cómo se utilizan en el diseñador.  
  
|Nombre de la propiedad|Obligatorio|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|La actividad para ejecutar mientras la condición es **true**. Para agregar la <xref:System.Activities.Statements.DoWhile.Body%2A> actividad, coloque una actividad en el cuadro de herramientas en el **cuerpo** cuadro en el **DoWhile** Diseñador de actividad con el texto de la sugerencia "Coloque la actividad aquí".|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|La condición que se va a evaluar tras cada una de las iteraciones del bucle. Para establecer el <xref:System.Activities.Statements.DoWhile.Condition%2A>, escriba un [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expresión en el **condición** cuadro en el **DoWhile** actividad diseñador o en la cuadrícula de propiedades.|  
  
## <a name="see-also"></a>Vea también  
 [While](../workflow-designer/while-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)