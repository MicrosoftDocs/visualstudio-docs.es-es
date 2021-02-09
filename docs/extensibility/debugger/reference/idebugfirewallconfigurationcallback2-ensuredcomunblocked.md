---
title: IDebugFirewallConfigurationCallback2::EnsureDCOMUnblocked
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EnsureDCOMUnblocked
- IDebugFirewallConfigurationCallback2::EnsureDCOMUnblocked
ms.assetid: acf54d27-32a6-47e7-aba6-3cc0004edc7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cdf9a98a3670da07b13590b8a8a6287ae783b76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869757"
---
# <a name="idebugfirewallconfigurationcallback2ensuredcomunblocked"></a>IDebugFirewallConfigurationCallback2::EnsureDCOMUnblocked

Solicita que el Firewall no bloquee la depuración remota.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnsureDCOMUnblocked(
    Void
);
```

```csharp
public int EnsureDCOMUnblocked();
```

## <a name="return-value"></a>Valor devuelto

 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también

- [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)
