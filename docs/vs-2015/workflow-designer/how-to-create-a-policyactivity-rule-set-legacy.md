---
title: Procedimiento Crear un conjunto de reglas para PolicyActivity (heredado) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8b5dc42932334b54bb46664da14af7df8dcfe131
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050791"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Procedimiento Crear un conjunto de reglas de PolicyActivity (heredado)
En este tema se describe cómo crear un conjunto de reglas de actividades de directiva mediante [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Una vez que haya arrastrado un **directiva** elemento de la actividad desde la **cuadro de herramientas** a la superficie de diseño de flujo de trabajo, deseará seleccionar una regla existente o cree un nuevo conjunto de reglas para la [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) actividad. Seleccione una regla existente establecida mediante el uso de la [seleccione Establecer cuadro de diálogo regla (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md) y crear conjuntos de reglas mediante el [cuadro de diálogo de Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Puede abrir el [cuadro de diálogo de Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) cuadro de diálogo directamente haciendo doble clic en un [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) actividad que se encuentra en la superficie de diseño de flujo de trabajo.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Para seleccionar o crear un conjunto de reglas para una actividad PolicyActivity  
  
1. Haga clic en el [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)y, a continuación, haga clic en **propiedades** para abrir el **propiedades** ventana.  
  
2. Haga clic en el **RuleSetReference** propiedad.  
  
3. Realice una de las siguientes acciones:  
  
    - Haga clic en el **RuleSetReference** elipses **[...]** y, a continuación, seleccione una regla existente establecida el [seleccione Establecer cuadro de diálogo regla (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md). A continuación, vaya al paso 10.  
  
         -o bien-  
  
    - Escriba un nombre para un conjunto de reglas. Haga clic en el **RuleSetReference** elipses **[...]** y, a continuación, seleccione **editar** en el [seleccione Establecer cuadro de diálogo regla (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         -o bien-  
  
    - Escriba un nombre para un conjunto de reglas. Expanda el **RuleSetReference** propiedad y seleccione el botón de puntos suspensivos **[...]**  en el **RuleSet Definition** propiedad.  
  
         El [cuadro de diálogo de Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) se abre.  
  
4. En el [cuadro de diálogo de Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), haga clic en **Agregar regla** para agregar una nueva regla al conjunto de reglas.  
  
5. Escriba el **nombre**, **prioridad**, y **reevaluación** propiedades, o mantenga los valores predeterminados.  
  
6. Escriba el texto para el **condición**.  
  
7. Escriba el texto para el **acciones Then** y **acciones Else**.  
  
8. Haga clic en **Agregar regla** nuevo para agregar otra regla.  
  
9. Cuando haya terminado, haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Cuadro de diálogo Establecer seleccione la regla (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Cuadro de diálogo del Editor (heredado) conjunto de reglas](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Uso de la actividad de directiva](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)