---
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f91ebbaa08d6e7d3de3b1a0c12ee7a774e0d16c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940324"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Habilita un motor de depuración que usa DCOM para solicitar [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] a la interfaz de usuario que se asegure de que el Firewall no bloqueará la depuración remota.

## <a name="syntax"></a>Sintaxis

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implementado por el objeto Port del administrador de depuración de la sesión.

## <a name="methods"></a>Métodos
 En la tabla siguiente se muestran los métodos de `IDebugFirewallConfigurationCallback2` .

|Método|Descripción|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Solicita que el Firewall no bloquee la depuración remota.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
