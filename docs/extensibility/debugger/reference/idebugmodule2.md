---
title: IDebugModule2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726909"
---
# <a name="idebugmodule2"></a>IDebugModule2
Esta interfaz representa un módulo, es decir, una unidad ejecutable de un programa, como un archivo DLL.

## <a name="syntax"></a>Sintaxis

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar un módulo y proporcionar acceso a la información sobre ese módulo.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Una llamada a [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) devuelve esta interfaz. El DE envía el [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) interfaz al administrador de depuración de sesión (SDM) mediante el [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método.

 Esta interfaz también se puede devolver en una estructura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) (que se devuelve mediante una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) también devuelve esta interfaz ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) devuelve el [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interfaz).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugModule2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Obtiene el [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) que describe este módulo.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETO. NO USAR. Vuelve a cargar los símbolos de este módulo.|

## <a name="remarks"></a>Observaciones
 La información del módulo se puede mostrar en la ventana **Módulos** del IDE.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
