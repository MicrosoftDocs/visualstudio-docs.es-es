---
title: Diseñador de actividad DoWhile | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 911e6d6d94090ddcdd43fcd9511624e209f7c03c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575432"
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
 [while](../workflow-designer/while-activity-designer.md)   
 [Flujo de control](../workflow-designer/control-flow-activity-designers.md)