---
description: Habilita un motor de depuración que usa DCOM para solicitar a la interfaz de usuario de Visual Studio que se asegure de que el Firewall no bloqueará la depuración remota.
title: IDebugFirewallConfigurationCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c67cc1ab9335cfeb197ca67937510b3137d6432c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073617"
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
