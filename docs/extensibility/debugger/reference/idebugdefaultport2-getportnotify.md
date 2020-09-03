---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 670dd128e6962c1e1d12f81eea03f9759fa56621
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732403"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Este método obtiene una interfaz [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) para este puerto.

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
enuncia Objeto [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Normalmente, `QueryInterface` se llama al método en el objeto que implementa la interfaz [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) para obtener una interfaz [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) . Sin embargo, hay circunstancias en las que la interfaz deseada se implementa en un objeto diferente. Este método oculta esas circunstancias y devuelve la `IDebugPortNotify2` interfaz del objeto más apropiado.

## <a name="see-also"></a>Vea también
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
