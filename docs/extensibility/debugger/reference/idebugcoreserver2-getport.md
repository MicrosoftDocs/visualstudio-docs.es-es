---
description: Recupera un puerto específico.
title: 'IDebugCoreServer2:: GetPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 481474ac56bdd77d63d6eeb256fac9ab356cc1aa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163205"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Recupera un puerto específico.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Parámetros
`guidPort`\
de GUID del puerto que se va a recuperar.

`ppPort`\
enuncia Devuelve un objeto [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa el puerto deseado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_PORTSUPPLIER_NO_PORT` si no hay ningún puerto con el identificador especificado.

## <a name="see-also"></a>Consulte también
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
