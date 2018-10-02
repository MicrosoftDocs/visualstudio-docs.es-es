---
title: Elija el cuadro de diálogo de operación (heredado) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 717fb2918c0532d85985a7b63f03a2e8bb397355
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566550"
---
# <a name="choose-operation-dialog-box-legacy"></a>Elegir operación (Cuadro de diálogo) (Heredado)
Este tema se describe cómo usar el **elegir operación** cuadro de diálogo heredado [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 El **elegir operación** cuadro de diálogo se utiliza para seleccionar una operación para asociar un <xref:System.Workflow.Activities.ReceiveActivity> actividad o un <xref:System.Workflow.Activities.SendActivity> actividad. Para obtener más información sobre cómo usar este cuadro de diálogo con esas actividades, consulte [Cómo: implementar una operación de contrato WCF (heredado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) y [Cómo: invocar una operación de contrato WCF (heredado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 La tabla siguiente describen los elementos de interfaz de usuario de la **elegir operación** cuadro de diálogo.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------|-----------------|  
|**Agregar contrato**|Crea un nuevo contrato. Puede definir las nuevas operaciones en este contrato. (Sólo se utiliza con <xref:System.Workflow.Activities.ReceiveActivity>.)|  
|**La operación de adición**|Agrega nuevas operaciones a un nuevo contrato que creó en el **elegir operación** cuadro de diálogo. **Nota:** puede agregar nuevas operaciones sólo a los contratos creados mediante el **elegir operación** cuadro de diálogo. <br /><br /> (Sólo se utiliza con <xref:System.Workflow.Activities.ReceiveActivity>.)|  
|**Importar...**|Importa un contrato previamente definido y permite seleccionar una operación desde ese contrato.|  
|**Nombre de la operación**|Nombre de la operación seleccionada actualmente. Este cuadro de texto está disponible para su edición solo si se ha creado una operación a través de la **elegir operación** cuadro de diálogo.|  
|**Parámetros**|Pestaña que contiene las definiciones de parámetro para la operación seleccionada actualmente. **Nota:** solo si ha creado una operación a través de las definiciones de parámetro que se pueden cambiar el **elegir operación** cuadro de diálogo.|  
|**Propiedades**|Pestaña que contiene los valores <xref:System.Net.Security.ProtectionLevel> para los mensajes enviados entre el cliente y el servicio. **Nota:** esta ficha solo está habilitada si se ha creado una operación a través de la **elegir operación** cuadro de diálogo.|  
|**Permisos**|Pestaña que contiene el <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> y las propiedades <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> de los usuarios que pueden llamar a esa operación. Por ejemplo, si solo los usuarios del grupo de administradores pueden llamar a esa operación, a continuación, se escribiría "Administradores" en el **rol** cuadro de texto.<br /><br /> Esta pestaña está habilitada para las dos operaciones creadas a través de la **ChooseOperation** cuadro de diálogo y las operaciones que se importaron a través de la **importación** botón.|  
  
> [!NOTE]
>  El **elegir operación** cuadro de diálogo sólo muestra contratos u operaciones utilizados por otras <xref:System.Workflow.Activities.SendActivity> las actividades del flujo de trabajo. De forma similar, el **elegir operación** cuadro de diálogo de <xref:System.Workflow.Activities.ReceiveActivity> actividades sólo muestra contratos u operaciones utilizados por otras **ReceiveActivity** actividades del flujo de trabajo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: implementar una operación de contrato WCF (heredado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Cómo: invocar una operación de contrato WCF (heredado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Ayuda de la interfaz de usuario del diseñador heredado para Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)