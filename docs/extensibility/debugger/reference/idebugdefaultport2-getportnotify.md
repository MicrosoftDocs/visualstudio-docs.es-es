---
description: Este método obtiene una interfaz IDebugPortNotify2 para este puerto.
title: 'IDebugDefaultPort2:: GetPortNotify | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd0d49275188eed1cebb7b1af3ee4dfcbb79cbe4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150658"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Este método obtiene una interfaz [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) para este puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parámetros
`ppPortNotify`\
enuncia Objeto [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Normalmente, `QueryInterface` se llama al método en el objeto que implementa la interfaz [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) para obtener una interfaz [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) . Sin embargo, hay circunstancias en las que la interfaz deseada se implementa en un objeto diferente. Este método oculta esas circunstancias y devuelve la `IDebugPortNotify2` interfaz del objeto más apropiado.

## <a name="see-also"></a>Consulte también
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
