---
title: Bind to an Activity&#39;s Property Dialog Box (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.ActivityBindForm.UI
helpviewer_keywords:
- Bind to an Activity's Property dialog box
ms.assetid: 19ebb207-e0a9-4642-8f5f-a5e31395c683
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 451544a84237bc6fa4e069df9dd1e17feccf86f7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301021"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Bind to an Activity&#39;s Property Dialog Box (Legacy)
This topic describes how use the **Bind to an Activity's Property** dialog box in the legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Un tipo de instancia de propiedad de dependencia se puede enlazar con la propiedad pública o evento de otra actividad. For more information about activity binding, see [Using Dependency Properties](https://go.microsoft.com/fwlink?LinkID=65007).

 You select a property to bind to using the **Bind to an Activity's Property** dialog box. You open this dialog box by clicking the ellipses **[…]** at the end of the selected property's text box in the **Properties** window, or by clicking the blue exclamation mark icon that appears next to the property name in the property browser.

 The following table describes the user interface (UI) elements of the **Bind to an Activity's Property** dialog box.

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Bind to an existing member**|Seleccione el miembro con el que desee enlazar en el panel de vista de árbol. El panel que hay debajo de la vista de árbol muestra un mensaje que indica si el miembro es de un tipo válido para enlazar o no. Click **OK** to bind to the selected valid member.|
|**Bind to a new member**|Cree un nuevo campo de miembro o propiedad con el que enlazar. Enter a **New Member Name**. Choose whether you want to create a dependency property or a public field by selecting **Create Field** or **Create Property**. Click **OK** to create the new member.|

## <a name="see-also"></a>Vea también
 [Using Activity Properties](https://go.microsoft.com/fwlink?LinkID=65013) [Using Dependency Properties](https://go.microsoft.com/fwlink?LinkID=65007) [Legacy Designer for Windows Workflow Foundation UI Help](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)