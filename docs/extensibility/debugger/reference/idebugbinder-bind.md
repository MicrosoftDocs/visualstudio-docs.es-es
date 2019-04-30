---
title: IDebugBinder::Bind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcb3535a2ace5818664a34a5d7b818d7dfd8b025
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877577"
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

#### <a name="parameters"></a>Parámetros
 `pContainer`

 [in] El [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que contiene el elemento secundario al que hace referencia `pField`.

 `pField`

 [in] El [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa el símbolo.

 `ppObject`

 [out] Devuelve el `IDebugObject` que representa la instancia del símbolo.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)