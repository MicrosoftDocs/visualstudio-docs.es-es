---
title: 'Cómo: crear un conjunto de reglas de PolicyActivity (heredado) | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c200c7db90f3cad12c1188af88f4651d2f2d44c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663388"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Cómo: Crear un conjunto de reglas para PolicyActivity (Heredado)
En este tema se describe cómo crear un conjunto de reglas de actividades de directiva mediante [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Una vez que haya arrastrado un elemento de actividad de **Directiva** desde el **cuadro de herramientas** a la superficie de diseño de flujo de trabajo, querrá seleccionar una regla existente o crear un nuevo conjunto de reglas para la actividad [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) . Puede seleccionar un conjunto de reglas existente mediante el [cuadro de diálogo Seleccionar conjunto de reglas (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md) y crear conjuntos de reglas mediante el [cuadro de diálogo Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Puede abrir el cuadro de diálogo [Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) directamente si hace doble clic en una actividad [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) que se encuentra en la superficie de diseño de flujo de trabajo.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Para seleccionar o crear un conjunto de reglas para una actividad PolicyActivity

1. Haga clic con el botón secundario en [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)y, a continuación, haga clic en **propiedades** para abrir la ventana **propiedades** .

2. Haga clic en la propiedad **RuleSetReference** .

3. Realice una de las siguientes acciones:

    - Haga clic en el **RuleSetReference** de puntos suspensivos **[...]** y, a continuación, seleccione un conjunto de reglas existente en el [cuadro de diálogo Seleccionar conjunto de reglas (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md). A continuación, vaya al paso 10.

         o bien

    - Escriba un nombre para un conjunto de reglas. Haga clic en el **RuleSetReference** de puntos suspensivos **[...]** y, a continuación, seleccione **Editar** en el [cuadro de diálogo Seleccionar conjunto de reglas (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         o bien

    - Escriba un nombre para un conjunto de reglas. Expanda la propiedad **RuleSetReference** y seleccione los puntos suspensivos **[...]** en la propiedad de **definición ruleset** .

         Se abre el [cuadro de diálogo Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) .

4. En el [cuadro de diálogo Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), haga clic en **Agregar regla** para agregar una nueva regla al conjunto de reglas.

5. Escriba las propiedades de **nombre**, **prioridad**y **reevaluación** , o mantenga los valores predeterminados.

6. Escriba el texto de la **condición**.

7. Escriba el texto para las **acciones then** y **else**.

8. Haga clic de nuevo en **Agregar regla** para agregar otra regla.

9. Cuando haya terminado, haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) cuadro de [diálogo Seleccionar conjunto de reglas (heredado)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [cuadro de diálogo Editor de conjunto de reglas (heredado)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [uso de la actividad directiva actividades de](http://go.microsoft.com/fwlink?LinkID=65004) [flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)