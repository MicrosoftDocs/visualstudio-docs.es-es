---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715568"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Esta interfaz enumera los programas que se ejecutan en la sesión de depuración actual.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) implementa esta interfaz para proporcionar una lista de los programas que va a depurar.

## <a name="notes-for-callers"></a>Notas para llamadores
 Visual Studio llama a [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) para obtener esta interfaz. Visual Studio no usa [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) .

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IEnumDebugPrograms2` .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera un número especificado de programas en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Omite un número especificado de programas en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtiene el número de programas de un enumerador.|

## <a name="remarks"></a>Observaciones
 Visual Studio usa esta interfaz para:

- Rellene la ventana **módulos** (llamando a [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) y llamando a [EnumModules (](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) en cada programa).

- Rellene la lista **asociar al proceso** (mediante una llamada a `IDebugProcess2::EnumPrograms` y, a continuación, llame a [QueryInterface](/cpp/atl/queryinterface) en cada interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para obtener una interfaz [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) ).

- Genera una lista de DEs que puede depurar cada programa en el proceso (mediante [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Aplique las actualizaciones de editar y continuar (ENC) a cada programa (llamando a IDebugProcess2:: EnumPrograms y llamando a [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
