---
title: IDebugFirewallConfigurationCallback2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1981d16141ed44ccbac0d2e05ae058451f0dff5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Permite que un motor de depuración que usa DCOM para pedir la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario para asegurarse de que el firewall no bloquee la depuración remota.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Implementada por el objeto de puerto de administrador de sesión de depuración.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugFirewallConfigurationCallback2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Solicitudes que el firewall no bloquea la depuración remota.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll