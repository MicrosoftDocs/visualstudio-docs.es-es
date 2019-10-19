---
title: Enlazar a una&#39;propiedad de Activity (cuadro de diálogo) (heredado) | Microsoft Docs
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
ms.openlocfilehash: b93f6787ef24a191385c0fd86672aa23ff72e3e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659215"
---
# <a name="bind-to-an-activity39s-property-dialog-box-legacy"></a>Enlazar a una&#39;propiedad de Activity (cuadro de diálogo) (heredado)
En este tema se describe cómo usar el cuadro de diálogo **enlazar a la propiedad de una actividad** en el [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Un tipo de instancia de propiedad de dependencia se puede enlazar con la propiedad pública o evento de otra actividad. Para obtener más información sobre el enlace de actividades, vea [usar propiedades de dependencia](http://go.microsoft.com/fwlink?LinkID=65007).

 Puede seleccionar una propiedad para enlazarla mediante el cuadro de diálogo **enlazar con la propiedad de una actividad** . Para abrir este cuadro de diálogo, haga clic en el botón de puntos suspensivos **[...]** al final del cuadro de texto de la propiedad seleccionada en la ventana **propiedades** o haga clic en el icono de signo de exclamación azul que aparece junto al nombre de la propiedad en el explorador de propiedades.

 En la tabla siguiente se describen los elementos de la interfaz de usuario (IU) del cuadro de diálogo **enlazar con la propiedad de una actividad** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Enlazar a un miembro existente**|Seleccione el miembro con el que desee enlazar en el panel de vista de árbol. El panel que hay debajo de la vista de árbol muestra un mensaje que indica si el miembro es de un tipo válido para enlazar o no. Haga clic en **Aceptar** para enlazar con el miembro válido seleccionado.|
|**Enlazar a un nuevo miembro**|Cree un nuevo campo de miembro o propiedad con el que enlazar. Escriba un **nuevo nombre de miembro**. Elija si desea crear una propiedad de dependencia o un campo público seleccionando **crear campo** o **crear propiedad**. Haga clic en **Aceptar** para crear el nuevo miembro.|

## <a name="see-also"></a>Vea también
 [Usar las propiedades de la actividad](http://go.microsoft.com/fwlink?LinkID=65013) [mediante propiedades](http://go.microsoft.com/fwlink?LinkID=65007) [de dependencia diseñador heredado para Windows Workflow Foundation ayuda de la interfaz de usuario](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)