---
title: IDebugProperty2::GetMemoryBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryBytes
helpviewer_keywords:
- IDebugProperty2::GetMemoryBytes
ms.assetid: b32042ed-7a06-4b4a-99ef-fe03b0aa61cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12d35ace2d5a2b2f0c10d4b2e0a44a05f52942fd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684135"
---
# <a name="idebugproperty2getmemorybytes"></a>IDebugProperty2::GetMemoryBytes
Obtiene los bytes de memoria que componen el valor de una propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetMemoryBytes ( 
   IDebugMemoryBytes2** ppMemoryBytes
);
```

```csharp
int GetMemoryBytes ( 
   out IDebugMemoryBytes2 ppMemoryBytes
);
```

#### <a name="parameters"></a>Parámetros
 `ppMemoryBytes`

 [out] Devuelve un [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objeto que puede usarse para recuperar la memoria que contiene el valor de la propiedad.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve el código de error. Devuelve `S_GETMEMORYBYTES_NO_MEMORY_BYTES` si no hay ningún byte de memoria para recuperar.

## <a name="see-also"></a>Vea también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)