---
title: "IDebugFirewallConfigurationCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugFirewallConfigurationCallback2"
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Habilita un motor de depuración que usa DCOM para solicitar la interfaz de usuario de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] para asegurarse de que un firewall no bloquee la depuración remota.  
  
## Sintaxis  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## Notas para los implementadores  
 Implementa el objeto de puerto del administrador de depuración de la sesión.  
  
## Métodos  
 La tabla siguiente se muestran los métodos de `IDebugFirewallConfigurationCallback2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Solicitudes que firewall no bloquee la depuración remota.|  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll