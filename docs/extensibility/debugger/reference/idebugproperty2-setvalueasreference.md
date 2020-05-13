---
title: IDebugProperty2::SetValueAsReference ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721248"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Establece el valor de esta propiedad en el valor de la referencia dada.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parámetros
`rgpArgs`\
[en] Matriz de argumentos para pasar al establecedor de propiedades de código administrado. Si el establecedor de propiedades no toma argumentos o si este [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto no hace referencia a dicho establecedor de propiedad, `rgpArgs` debe ser un valor nulo. Este parámetro suele ser un valor nulo.

`dwArgCount`\
[en] El número de argumentos de la `rgpArgs` matriz.

`pValue`\
[en] Una referencia, en forma de un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto, al valor que se usará para establecer esta propiedad.

`dwTimeout`\
[en] Cuánto tiempo se tarda en establecer el valor, en milisegundos. Un valor `INFINITE`típico es . Esto afecta al tiempo que puede tardar cualquier evaluación posible.

## <a name="return-value"></a>Valor devuelto
 Si se `S_OK`realiza correctamente, devuelve ; de lo contrario devuelve un código de error, normalmente uno de los siguientes:

|Error|Descripción|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|No se admite establecer el valor de una referencia.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|El valor no se puede establecer, ya que esta propiedad hace referencia a un método.|
|`E_SETVALUE_VALUE_IS_READONLY`|El valor es de solo lectura y no se puede establecer.|
|`E_NOTIMPL`|El método no está implementado.|

## <a name="see-also"></a>Vea también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
