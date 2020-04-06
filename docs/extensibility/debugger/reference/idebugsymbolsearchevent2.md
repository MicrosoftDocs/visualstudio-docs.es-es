---
title: IDebugSymbolSearchEvent2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbe99422e506fb86b0a7e1d9d3242783f3258e6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718788"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Esta interfaz es enviada por el motor de depuración (DE) para indicar que se han cargado los símbolos de depuración para un módulo que se está depurando.

## <a name="syntax"></a>Sintaxis

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para informar de que se han cargado los símbolos de un módulo. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz. El SDM utiliza [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 La DE crea y envía este objeto de evento para informar de que se han cargado los símbolos de un módulo. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La `IDebugSymbolSearchEvent2` interfaz expone el siguiente método.

|Método|Descripción|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Recupera información sobre los resultados de una búsqueda de símbolos.|

## <a name="remarks"></a>Observaciones
 Este evento se enviará incluso si los símbolos no se han podido cargar. La `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` llamada permite al controlador de este evento determinar si el módulo realmente tiene símbolos.

 Visual Studio normalmente usa este evento para actualizar el estado de los símbolos cargados en el **módulos** ventana.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
