---
description: El motor DE depuración (DE) envía esta interfaz al administrador de depuración de sesión (SDM) cuando se carga o descarga un módulo.
title: IDebugModuleLoadEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2
helpviewer_keywords:
- IDebugModuleLoadEvent2 interface
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 59b5e9e7619434b9ff4d914fc7b955ebbab4ace2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149852"
---
# <a name="idebugmoduleloadevent2"></a>IDebugModuleLoadEvent2
El motor DE depuración (DE) envía esta interfaz al administrador de depuración de sesión (SDM) cuando se carga o descarga un módulo.

## <a name="syntax"></a>Syntax

```
IDebugModuleLoadEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para informar de que un módulo se ha cargado o descargado. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 El DE crea y envía este objeto de evento para informar de que un módulo se ha cargado o descargado. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestra el método de `IDebugModuleLoadEvent2` .

|Método|Descripción|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|Obtiene el módulo que se está cargando o descargando.|

## <a name="remarks"></a>Observaciones
 Visual Studio usa este evento para mantener actualizada la ventana **módulos** .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
