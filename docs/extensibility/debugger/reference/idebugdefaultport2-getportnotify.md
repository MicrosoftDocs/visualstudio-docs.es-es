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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ed43d96a7035dbd9e75a8e64a23e556997e087c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077478"
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
