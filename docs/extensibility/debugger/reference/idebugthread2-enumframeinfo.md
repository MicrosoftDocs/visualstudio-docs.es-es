---
description: Recupera una lista de los marcos de pila para este subproceso.
title: 'IDebugThread2:: EnumFrameInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9ad740de00338596de622cbce1028768ddda638
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149345"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Recupera una lista de los marcos de pila para este subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`dwFieldSpec`\
de Combinación de marcas de la enumeración [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica los campos de las estructuras [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que se van a rellenar. Especifique la `FIF_FUNCNAME_FORMAT` marca para dar formato al nombre de la función en una sola cadena.

`nRadix`\
de Base usada para dar formato a la información numérica en el enumerador.

`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) que contiene una lista de estructuras [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que describe el marco de pila.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Los fotogramas del subproceso se enumeran en orden, con el fotograma actual enumerado primero y el fotograma más antiguo enumerado en último lugar.

## <a name="see-also"></a>Consulte también
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
