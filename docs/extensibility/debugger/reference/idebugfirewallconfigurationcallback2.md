---
title: IDebugFirewallConfigurationCallback2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 635771fc87326b28566058a43d4922b131ae1975
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728716"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Habilita un motor de depuración [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] que usa DCOM para pedir a la interfaz de usuario que se asegure de que el firewall no bloqueará la depuración remota.

## <a name="syntax"></a>Sintaxis

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implementado por el objeto de puerto del administrador de depuración de sesión.

## <a name="methods"></a>Métodos
 En la tabla siguiente `IDebugFirewallConfigurationCallback2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Solicita que el firewall no bloquee la depuración remota.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
