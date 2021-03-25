---
description: Establece el valor de esta propiedad en el valor de la referencia especificada.
title: 'IDebugProperty2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8b370b4caa43ce6522b415233714eb15899b3051
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064779"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Establece el valor de esta propiedad en el valor de la referencia especificada.

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
de Matriz de argumentos que se va a pasar al establecedor de propiedad de código administrado. Si el establecedor de propiedad no toma argumentos o si este objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) no hace referencia a este tipo de establecedor de propiedad, `rgpArgs` debe ser un valor null. Este parámetro suele ser un valor null.

`dwArgCount`\
de El número de argumentos de la `rgpArgs` matriz.

`pValue`\
de Una referencia, en forma de un objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , al valor que se va a usar para establecer esta propiedad.

`dwTimeout`\
de Cuánto tiempo se debe llevar a cabo para establecer el valor, en milisegundos. Un valor típico es `INFINITE` . Esto afecta a la cantidad de tiempo que puede tardar cualquier posible evaluación.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error, normalmente uno de los siguientes:

|Error|Descripción|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|No se admite establecer el valor de una referencia.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|No se puede establecer el valor, ya que esta propiedad hace referencia a un método.|
|`E_SETVALUE_VALUE_IS_READONLY`|El valor es de solo lectura y no se puede establecer.|
|`E_NOTIMPL`|El método no está implementado.|

## <a name="see-also"></a>Consulte también
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
