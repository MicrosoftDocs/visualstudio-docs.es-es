---
title: IDebugMemoryBytes2::ReadAt ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727535"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lee una secuencia de bytes, comenzando en una ubicación determinada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>Parámetros
`pStartContext`\
[en] El [objeto IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que especifica dónde empezar a leer bytes.

`dwCount`\
[en] El número de bytes que se van a leer. También especifica la longitud `rgbMemory` de la matriz.

`rgbMemory`\
[adentro, fuera] Matriz rellenada con los bytes realmente leídos.

`pdwRead`\
[fuera] Devuelve el número de bytes contiguos realmente leídos.

`pdwUnreadable`\
[adentro, fuera] Devuelve el número de bytes ilegibles. Puede ser un valor nulo si el cliente no está interesado en el número de bytes ilegibles.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Si se solicitan 100 bytes y los primeros 50 son legibles, los 20 siguientes son ilegibles y los 30 restantes son legibles, este método devuelve:

 *`pdwRead`50

 *`pdwUnreadable`20

 En este caso, porque `*pdwRead + *pdwUnreadable < dwCount`, el llamador debe realizar una llamada adicional para leer los 30 bytes restantes de los 100 originales solicitados y el [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto pasado en el `pStartContext` parámetro debe ser avanzado por 70.

## <a name="see-also"></a>Vea también
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
