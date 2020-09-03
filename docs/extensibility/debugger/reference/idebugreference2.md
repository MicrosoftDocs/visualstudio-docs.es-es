---
title: IDebugReference2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720266"
---
# <a name="idebugreference2"></a>IDebugReference2
Esta interfaz representa una referencia a una propiedad de marco de pila o alguna otra propiedad.

> [!NOTE]
> `IDebugReference2` está reservado para un uso futuro y todos sus métodos deben devolver `E_NOTIMPL` .

## <a name="syntax"></a>Sintaxis

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para representar una referencia a un tipo de valor determinado. Por ejemplo, el valor podría ser un valor numérico como resultado de una evaluación de expresión, un contexto de memoria utilizado para mostrar memoria o una lista de registros y sus valores.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) para obtener esta interfaz. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) y [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) también devuelven esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugReference2` .

|Método|Descripción|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Obtiene la estructura de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) que describe esta referencia.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Establece el valor de esta referencia a partir de una cadena.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Establece el valor de esta referencia desde otra referencia.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Enumera los elementos secundarios de esta referencia.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Obtiene el elemento primario de esta referencia.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Obtiene la referencia más derivada de esta referencia.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Obtiene los bytes de memoria a los que se refiere esta referencia.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Obtiene un contexto de memoria para esta referencia.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Obtiene el tamaño, en bytes, de esta referencia.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Establece este tipo de referencia.|
|[Comparar](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Compara esta referencia con otra.|

## <a name="remarks"></a>Observaciones

> [!NOTE]
> Este uso de "propiedad" no se debe confundir con, lo que significa una variable miembro de una clase, aunque un `IDebugReference2` puede representar tal entidad.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) representa una propiedad, mientras que `IDebugReference2` representa una referencia a una propiedad, normalmente una referencia a un objeto en el programa que se está depurando.

 La diferencia principal entre una propiedad y una referencia es que una propiedad hace referencia a una instancia con nombre de un objeto, mientras que una referencia se refiere a una instancia sin nombre. Por ejemplo, una propiedad puede hacer referencia a un objeto en el montón del programa mediante `"a.b"` . Otra propiedad puede hacer referencia al mismo objeto que `"c.d"` . La manera de hacer referencia a esta propiedad requiere que `"a.b"` o `"c.d"` estén en el ámbito. Una referencia a este mismo objeto no tiene nombre. se puede hacer referencia al objeto siempre que la memoria de ese objeto sea válida.

 Una `IDebugProperty2` interfaz se puede considerar como un valor con un nombre, un tipo y una dirección. `IDebugReference2`Por otro lado, se puede considerar como un tipo y una dirección.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
