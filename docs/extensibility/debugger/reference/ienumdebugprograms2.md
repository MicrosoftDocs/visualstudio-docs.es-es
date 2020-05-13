---
title: IEnumDebugPrograms2 ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715568"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Esta interfaz enumera los programas que se ejecutan en la sesión de depuración actual.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para proporcionar una lista de programas que está depurando el DE.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Visual Studio llama a [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) para obtener esta interfaz. Visual Studio no usa [EnumPrograms.](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IEnumDebugPrograms2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera un número especificado de programas en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Omite un número especificado de programas en una secuencia de enumeración.|
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtiene el número de programas en un enumerador.|

## <a name="remarks"></a>Observaciones
 Visual Studio usa esta interfaz para:

- Rellene la ventana **Módulos** (llamando a [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) y, a continuación, llamando a [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) en cada programa).

- Rellenar el **asociar al** proceso `IDebugProcess2::EnumPrograms` lista (mediante una llamada y, a continuación, llamar a [QueryInterface](/cpp/atl/queryinterface) en cada [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz para obtener un [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interfaz).

- Genere una lista de DE que pueden depurar cada programa en el proceso (mediante [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Aplique las actualizaciones de Editar y continuar (ENC) a cada programa (mediante una llamada a IDebugProcess2::EnumPrograms y, a continuación, llamando a [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
