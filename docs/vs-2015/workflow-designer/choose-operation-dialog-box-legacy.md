---
title: Cuadro de diálogo elegir operación (heredado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659163"
---
# <a name="choose-operation-dialog-box-legacy"></a>Elegir operación (Cuadro de diálogo) (Heredado)
En este tema se describe cómo usar el cuadro de diálogo **elegir operación** en el [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 El cuadro de diálogo **elegir operación** se usa para seleccionar una operación que se va a asociar a una actividad <xref:System.Workflow.Activities.ReceiveActivity> o a una actividad <xref:System.Workflow.Activities.SendActivity>. Para obtener más información sobre el uso de este cuadro de diálogo con esas actividades, vea [Cómo: implementar una operación de contrato WCF (heredado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) y [Cómo: invocar una operación de contrato WCF (heredado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 En la tabla siguiente se describen los elementos de la interfaz de usuario (UI) del cuadro de diálogo **elegir operación** .

|Elemento de la interfaz de usuario|Descripción|
|----------------|-----------------|
|**Agregar contrato**|Crea un nuevo contrato. Puede definir las nuevas operaciones en este contrato. (Sólo se utiliza con <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Agregar operación**|Agrega nuevas operaciones a un nuevo contrato creado en el cuadro de diálogo **elegir operación** . **Nota:**  Puede agregar nuevas operaciones solo a los contratos creados mediante el cuadro de diálogo **elegir operación** . <br /><br /> (Sólo se utiliza con <xref:System.Workflow.Activities.ReceiveActivity>.)|
|**Importar...**|Importa un contrato previamente definido y permite seleccionar una operación desde ese contrato.|
|**Nombre de la operación**|Nombre de la operación seleccionada actualmente. Este cuadro de texto solo está disponible para su edición si se ha creado una operación mediante el cuadro de diálogo **elegir operación** .|
|**Parámetros**|Pestaña que contiene las definiciones de parámetro para la operación seleccionada actualmente. **Nota:**  Las definiciones de parámetros solo se pueden cambiar si se ha creado una operación mediante el cuadro de diálogo **elegir operación** .|
|**Propiedades**|Pestaña que contiene los valores <xref:System.Net.Security.ProtectionLevel> para los mensajes enviados entre el cliente y el servicio. **Nota:**  Esta pestaña solo está habilitada si se ha creado una operación mediante el cuadro de diálogo **elegir operación** .|
|**Permisos**|Pestaña que contiene el <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> y las propiedades <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> de los usuarios que pueden llamar a esa operación. Por ejemplo, si solo los usuarios del grupo administradores podían llamar a esa operación, escribiría "administradores" en el cuadro de texto **rol** .<br /><br /> Esta pestaña está habilitada para las dos operaciones creadas mediante el cuadro de diálogo **ChooseOperation** y las operaciones que se importaron mediante el botón **importar** .|

> [!NOTE]
> En el cuadro de diálogo **elegir operación** solo se muestran los contratos u operaciones utilizados por otras actividades de <xref:System.Workflow.Activities.SendActivity> en el flujo de trabajo. Del mismo modo, el cuadro de diálogo **elegir operación** para actividades de <xref:System.Workflow.Activities.ReceiveActivity> muestra solo contratos u operaciones que usan otras actividades de **ReceiveActivity** en el flujo de trabajo.

## <a name="see-also"></a>Vea también
 [Cómo: implementar una operación de contrato WCF (heredado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [Cómo: invocar un diseñador heredado de operación de contrato WCF (heredado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [para obtener Windows Workflow Foundation ayuda de la interfaz de usuario](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)