---
title: IDebugModuleLoadEvent2::GetModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ee91686051440fe44efd1f4e4f9ba933f3e0c99
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323700"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Obtiene el módulo que se carga o descarga.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Parámetros
`pModule`\
[out] Devuelve un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) objeto que representa el módulo que se carga o descarga.

`pbstrDebugMessage`\
[in, out] Devuelve un mensaje opcional que describe este evento. Si este parámetro es un valor null, no se solicita ningún mensaje.

`pbLoad`\
[in, out] Distinto de cero (`TRUE`) si el módulo se carga y cero (`FALSE`) si se está descargando el módulo. Si este parámetro es un valor null, no se solicita ningún estado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)