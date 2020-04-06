---
title: IDebugReference2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720266"
---
# <a name="idebugreference2"></a>IDebugReference2
Esta interfaz representa una referencia a una propiedad de marco de pila o alguna otra propiedad.

> [!NOTE]
> `IDebugReference2`está reservado para uso futuro, y `E_NOTIMPL`todos sus métodos deben devolver .

## <a name="syntax"></a>Sintaxis

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 La DE implementa esta interfaz para representar una referencia a un tipo determinado de valor. Por ejemplo, el valor podría ser un valor numérico como resultado de una evaluación de expresión, un contexto de memoria utilizado para mostrar memoria o una lista de registros y sus valores.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) para obtener esta interfaz. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) y [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) también devuelven esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugReference2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Obtiene la [estructura DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) que describe esta referencia.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Establece el valor de esta referencia a partir de una cadena.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Establece el valor de esta referencia a partir de otra referencia.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera los elementos secundarios de esta referencia.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Obtiene el elemento primario de esta referencia.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Obtiene la referencia más derivada de esta referencia.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtiene los bytes de memoria a los que hace referencia esta referencia.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Obtiene un contexto de memoria para esta referencia.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Obtiene el tamaño, en bytes, de esta referencia.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Establece este tipo de referencia.|
|[Comparar](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Compara esta referencia con otra.|

## <a name="remarks"></a>Observaciones

> [!NOTE]
> Este uso de "propiedad" no debe confundirse con ese significado `IDebugReference2` una variable miembro de una clase, aunque un puede representar tal entidad.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) representa una propiedad, mientras `IDebugReference2` que representa una referencia a una propiedad, normalmente una referencia a un objeto en el programa que se está depurando.

 La principal diferencia entre una propiedad y una referencia es que una propiedad hace referencia a una instancia con nombre de un objeto, mientras que una referencia hace referencia a una instancia sin nombre. Por ejemplo, una propiedad puede hacer referencia a `"a.b"`un objeto en el montón del programa por . Otra propiedad puede hacer referencia `"c.d"`al mismo objeto que . La forma de hacer referencia `"a.b"` a `"c.d"` esta propiedad requiere que o esté en el ámbito. Una referencia a este mismo objeto no tiene nombre; se puede hacer referencia al objeto siempre que la memoria de ese objeto sea válida.

 Una `IDebugProperty2` interfaz se puede considerar como un valor con un nombre, un tipo y una dirección. Un `IDebugReference2`, por otro lado, se puede considerar como un tipo y una dirección.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
