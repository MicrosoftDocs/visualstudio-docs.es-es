---
title: IDebugBinder::Bind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00d7e63b8a521ee25d2c7d378aeb82d064358ec9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344504"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Este método obtiene el contexto de la memoria o un objeto que contiene el valor actual del símbolo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parámetros
`pContainer`\
[in] El [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que contiene el elemento secundario al que hace referencia `pField`.

`pField`\
[in] El [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el símbolo.

`ppObject`\
[out] Devuelve el `IDebugObject` que representa la instancia del símbolo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)