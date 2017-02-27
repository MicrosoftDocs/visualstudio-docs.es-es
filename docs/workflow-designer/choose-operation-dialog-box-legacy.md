---
title: "Elegir operaci&#243;n (Cuadro de di&#225;logo) (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Design.OperationPickerDialog.UI"
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Elegir operaci&#243;n (Cuadro de di&#225;logo) (Heredado)
En este tema se describe el uso del cuadro de diálogo **Elegir operación** en [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado.Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 El cuadro de diálogo **Elegir operación** se usa para seleccionar una operación y asociarla a una actividad <xref:System.Workflow.Activities.ReceiveActivity> o una actividad <xref:System.Workflow.Activities.SendActivity>.Para obtener más información acerca de cómo utilizar este cuadro de diálogo con esas actividades, vea [Cómo: Implementar una operación de contrato WCF \(Heredado\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) y [Cómo: Invocar una operación de contrato WCF \(Heredado\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 En la siguiente tabla se describe los elementos de la interfaz de usuario \(IU\) del cuadro de diálogo **Elegir operación**.  
  
|Elemento de la interfaz de usuario|Descripción|  
|----------------------------------------|-----------------|  
|**Agregar contacto**|Crea un nuevo contrato.Puede definir las nuevas operaciones en este contrato.\(Sólo se utiliza con <xref:System.Workflow.Activities.ReceiveActivity>.\)|  
|**Agregar operación**|Agrega nuevas operaciones al nuevo contrato creado en el cuadro de diálogo **Elegir operación**. **Note:**  Las nuevas operaciones sólo pueden agregarse a los contratos creados mediante el cuadro de diálogo **Elegir operación**. <br /><br /> \(Sólo se utiliza con <xref:System.Workflow.Activities.ReceiveActivity>.\)|  
|**Importar...**|Importa un contrato previamente definido y permite seleccionar una operación desde ese contrato.|  
|**Nombre de la operación**|Nombre de la operación seleccionada actualmente.Este cuadro de texto sólo está disponible para edición si se ha creado una operación mediante el cuadro de diálogo **Elegir operación**.|  
|**Parámetros**|Pestaña que contiene las definiciones de parámetro para la operación seleccionada actualmente. **Note:**  Las definiciones de parámetro sólo pueden cambiarse si se ha creado una operación mediante el cuadro de diálogo **Elegir operación**.|  
|**Propiedades**|Pestaña que contiene los valores <xref:System.Net.Security.ProtectionLevel> para los mensajes enviados entre el cliente y el servicio. **Note:**  Esta pestaña sólo se habilita si se ha creado una operación mediante el cuadro de diálogo **Elegir operación**.|  
|**Permisos**|Pestaña que contiene el <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> y las propiedades <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> de los usuarios que pueden llamar a esa operación.Por ejemplo, si sólo pueden llamar a esa operación los usuarios del grupo de administradores, deberá escribir “Administradores” el cuadro de texto **Rol**.<br /><br /> Esta pestaña está habilitada para las dos operaciones creadas mediante el cuadro de diálogo **Elegiroperación**, y las operaciones importadas utilizando el botón **Importar**.|  
  
> [!NOTE]
>  El cuadro de diálogo **Elegir operación** sólo muestra contratos u operaciones utilizados por otras actividades <xref:System.Workflow.Activities.SendActivity> del flujo de trabajo.De igual modo, el cuadro de diálogo **Elegir operación** para las actividades <xref:System.Workflow.Activities.ReceiveActivity> sólo muestra contratos u operaciones utilizados por otras actividades **ReceiveActivity** del flujo de trabajo.  
  
## Vea también  
 [Cómo: Implementar una operación de contrato WCF \(Heredado\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Cómo: Invocar una operación de contrato WCF \(Heredado\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Ayuda de la interfaz de usuario del diseñador heredado para Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)