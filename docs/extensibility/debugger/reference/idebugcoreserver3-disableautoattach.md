---
description: Deshabilita la Asociación automática de todos los motores de depuración asociados con este servidor.
title: IDebugCoreServer3::D isableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DisableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::DisableAutoAttach
ms.assetid: 9d860a20-c154-4df4-ba15-636e0fcd42bf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ad02efc68fe0bdd7a64ae0df02fe934a2044abc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154722"
---
# <a name="idebugcoreserver3disableautoattach"></a>IDebugCoreServer3::DisableAutoAttach
Deshabilita la Asociación automática de todos los motores de depuración asociados con este servidor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT DisableAutoAttach(
   void
);
```

```csharp
int DisableAutoAttach();
```

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.

## <a name="see-also"></a>Consulte también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
