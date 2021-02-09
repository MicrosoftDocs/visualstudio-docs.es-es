---
title: 'IDebugReference2:: GetReferenceInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca23c5acd5f32d79cb76f2059b6a39066197150f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896043"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Obtiene la estructura de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) que describe una referencia. Reservado para un uso futuro.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetReferenceInfo ( 
   DEBUGREF_INFO_FLAGS   dwFields,
   DWORD                 nRadix,
   DWORD                 dwTimeout,
   IDebugReference2**    rgpArgs,
   DWORD                 dwArgCount,
   DEBUG_REFERENCE_INFO* pReferenceInfo
);
```

```csharp
int GetReferenceInfo ( 
   enum_DEBUGREF_INFO_FLAGS  dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_REFERENCE_INFO[]    pReferenceInfo
);
```

## <a name="parameters"></a>Parámetros
`dwFields`\
de Combinación de marcas de la enumeración [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) que determina los campos que se van a rellenar en la estructura de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .

`nRadix`\
de La base que se va a utilizar para dar formato a cualquier información numérica.

`dwTimeout`\
de Tiempo máximo, en milisegundos, que se va a esperar antes de que se devuelva desde este método. Use `INFINITE` para esperar indefinidamente.

`rgpArgs`\
de Matriz de objetos [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Reservado para uso futuro; establecer en un valor null.

`dwArgCount`\
de El número de argumentos de referencia de la `rgpArgs` matriz. Reservado para uso futuro; establézcalo en 0.

`pReferenceInfo`\
enuncia [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructura que se rellena con una descripción de la propiedad.

## <a name="return-value"></a>Valor devuelto
 Siempre devuelve `E_NOTIMPL`.

## <a name="see-also"></a>Vea también
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
