---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7dee04516d8bc8d72859509a9f721455d858a433
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929399"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Esta interfaz enumera los contextos de código asociados a la sesión de depuración o con un programa o un documento determinados.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) implementa esta interfaz para representar una lista de contextos de código para una posición de texto determinada en un programa, o una lista de contextos de código para un contexto de documento determinado.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para obtener esta interfaz que representa una lista de contextos de código para una posición de texto específica en el documento de origen de un programa.

 Llame a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) para obtener esta interfaz que representa una lista de todos los contextos de código de un documento de origen determinado.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IEnumDebugCodeContexts2` .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera un número especificado de contextos de código en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Omite un número especificado de contextos de código en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtiene el número de contextos de código en un enumerador.|

## <a name="remarks"></a>Notas
 Visual Studio llama a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para rellenar una lista de contextos de código que el usuario puede elegir al establecer la siguiente instrucción o mostrar el desensamblado de un archivo de código fuente. Se pueden producir varios contextos de código, por ejemplo, cuando hay varias instancias de una plantilla de estilo C++.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
