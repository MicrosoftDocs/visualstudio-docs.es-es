---
title: "Cómo: crear un conjunto de reglas para PolicyActivity (heredado) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 49c511c2d881a9996efe07dcc030e80e21a8cf88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Cómo: Crear un conjunto de reglas para PolicyActivity (Heredado)
En este tema se describe cómo crear un conjunto de reglas de actividades de directiva mediante [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Una vez que haya arrastrado un **directiva** elemento de la actividad de la **cuadro de herramientas** a la superficie de diseño de flujo de trabajo, deberá seleccionar una regla existente o crear un nuevo conjunto de reglas para la [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) actividad. Seleccione una regla existente que se establece mediante el [regla establecer cuadro de diálogo Seleccionar (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md) y crear conjuntos de reglas mediante el [cuadro de diálogo de Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Puede abrir el [cuadro de diálogo de Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) cuadro de diálogo directamente haciendo doble clic en un [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) actividad que se encuentra en la superficie de diseño de flujo de trabajo.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Para seleccionar o crear un conjunto de reglas para una actividad PolicyActivity  
  
1.  Haga clic en el [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)y, a continuación, haga clic en **propiedades** para abrir el **propiedades** ventana.  
  
2.  Haga clic en el **RuleSetReference** propiedad.  
  
3.  Realice una de las siguientes acciones:  
  
    -   Haga clic en el **RuleSetReference** puntos suspensivos **[...]** y, a continuación, seleccione una regla existente establecida el [regla establecer cuadro de diálogo Seleccionar (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md). A continuación, vaya al paso 10.  
  
         o bien  
  
    -   Escriba un nombre para un conjunto de reglas. Haga clic en el **RuleSetReference** puntos suspensivos **[...]** y, a continuación, seleccione **editar** en el [regla establecer cuadro de diálogo Seleccionar (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         O bien  
  
    -   Escriba un nombre para un conjunto de reglas. Expanda el **RuleSetReference** propiedad y seleccione los puntos suspensivos **[...]**  en el **RuleSet Definition** propiedad.  
  
         El [cuadro de diálogo de Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) se abre.  
  
4.  En el [cuadro de diálogo de Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), haga clic en **Agregar regla** para agregar una nueva regla para el conjunto de reglas.  
  
5.  Escriba el **nombre**, **prioridad**, y **reevaluación** propiedades, o mantenga los valores predeterminados.  
  
6.  Escriba el texto para el **condición**.  
  
7.  Escriba el texto para el **acciones Then** y **acciones Else**.  
  
8.  Haga clic en **Agregar regla** nuevo para agregar otra regla.  
  
9. Cuando haya terminado, haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Cuadro de diálogo Seleccione la regla establecer (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Conjunto de reglas de cuadro de diálogo de Editor (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Uso de la actividad de directiva](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)