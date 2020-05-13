---
title: IDebugDefaultPort2::GetPortNotify ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 670dd128e6962c1e1d12f81eea03f9759fa56621
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732403"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Este método obtiene un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaz para este puerto.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

## <a name="parameters"></a>Parámetros
`ppPortNotify`\
[fuera] Un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) objeto.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Normalmente, `QueryInterface` se llama al método en el objeto que implementa el [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz para obtener un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaz. Sin embargo, hay circunstancias en las que la interfaz deseada se implementa en un objeto diferente. Este método oculta esas circunstancias `IDebugPortNotify2` y devuelve la interfaz del objeto más adecuado.

## <a name="see-also"></a>Vea también
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
