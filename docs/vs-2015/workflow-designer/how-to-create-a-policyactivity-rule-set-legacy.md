---
title: 'How to: Create a PolicyActivity Rule Set (Legacy) | Microsoft Docs'
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
ms.openlocfilehash: 1c18a08986bf8e4aa30969a9d30d740fb68e978c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297476"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Cómo: Crear un conjunto de reglas para PolicyActivity (Heredado)
En este tema se describe cómo crear un conjunto de reglas de actividades de directiva mediante [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 After you have dragged a **Policy** activity item from the **Toolbox** to the workflow design surface, you will want to select an existing rule or create a new rule set for the [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) activity. You select an existing rule set by using the [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) and you create rule sets by using the [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> You can open the [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) dialog box directly by double-clicking on a [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) activity that is on the workflow design surface.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Para seleccionar o crear un conjunto de reglas para una actividad PolicyActivity

1. Right-click the [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019), and then click **Properties** to open the **Properties** window.

2. Click the **RuleSetReference** property.

3. Realice una de las siguientes acciones:

    - Click the **RuleSetReference** ellipses **[…]** , and then select an existing rule set in the [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md). A continuación, vaya al paso 10.

         o bien

    - Escriba un nombre para un conjunto de reglas. Click the **RuleSetReference** ellipses **[…]** , and then select **Edit** in the [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         o bien

    - Escriba un nombre para un conjunto de reglas. Expand the **RuleSetReference** property and select the ellipses **[…]** in the **RuleSet Definition** property.

         The [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) opens.

4. In the [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), click **Add Rule** to add a new rule to the rule set.

5. Enter the **Name**, **Priority**, and **Reevaluation** properties, or keep the default values.

6. Enter the text for the **Condition**.

7. Enter the text for the **Then Actions** and the **Else Actions**.

8. Click **Add Rule** again to add another rule.

9. When you are finished, click **OK**.

## <a name="see-also"></a>Vea también
 [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [Using the Policy Activity](https://go.microsoft.com/fwlink?LinkID=65004) [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md)