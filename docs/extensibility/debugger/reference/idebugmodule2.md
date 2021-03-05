---
description: Esta interfaz representa un módulo, es decir, una unidad ejecutable de un programa, como un archivo DLL.
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7cc14d4f33924a04b25344c4c624a633b97ff7b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150489"
---
# <a name="idebugmodule2"></a>IDebugModule2
Esta interfaz representa un módulo, es decir, una unidad ejecutable de un programa, como un archivo DLL.

## <a name="syntax"></a>Syntax

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) implementa esta interfaz para representar un módulo y proporcionar acceso a la información sobre ese módulo.

## <a name="notes-for-callers"></a>Notas para llamadores
 Una llamada a [getModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) devuelve esta interfaz. El DE envía la interfaz [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) al administrador de depuración de la sesión (SDM) mediante el método de [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .

 Esta interfaz también se puede devolver en una estructura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) (devuelta por una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) también devuelve esta interfaz ([EnumModules (](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) devuelve la interfaz [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) ).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugModule2` .

|Método|Descripción|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Obtiene el [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) que describe este módulo.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETO. NO USE. Vuelve a cargar los símbolos para este módulo.|

## <a name="remarks"></a>Observaciones
 La información del módulo se puede mostrar en la ventana **módulos** del IDE.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
