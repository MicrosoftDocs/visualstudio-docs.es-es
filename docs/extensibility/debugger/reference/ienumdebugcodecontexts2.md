---
title: IEnumDebugCodeContexts2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717271"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Esta interfaz enumera los contextos de código asociados con la sesión de depuración o con un programa o documento determinado.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar una lista de contextos de código para una posición de texto determinada en un programa, o una lista de contextos de código para un contexto de documento determinado.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para obtener esta interfaz que representa una lista de contextos de código para una posición de texto específica en el documento de origen de un programa.

 Llame a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) para obtener esta interfaz que representa una lista de todos los contextos de código en un documento de origen determinado.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IEnumDebugCodeContexts2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera un número especificado de contextos de código en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Omite un número especificado de contextos de código en una secuencia de enumeración.|
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtiene el número de contextos de código en un enumerador.|

## <a name="remarks"></a>Observaciones
 Visual Studio llama a [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para rellenar una lista de contextos de código que el usuario puede elegir al establecer la siguiente instrucción o mostrar el desensamblado de un archivo de origen. Pueden producirse varios contextos de código, por ejemplo, cuando hay varias instancias de una plantilla de estilo C++.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
