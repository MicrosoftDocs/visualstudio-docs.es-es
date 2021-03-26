---
description: Esta interfaz representa un módulo que admite ubicaciones alternativas de símbolos y Estados JustMyCode.
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0ccac9c260619b21079c6a277d842d322750cbc1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065494"
---
# <a name="idebugmodule3"></a>IDebugModule3
Esta interfaz representa un módulo que admite ubicaciones alternativas de símbolos y Estados JustMyCode.

## <a name="syntax"></a>Sintaxis

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) implementa esta interfaz para admitir ubicaciones alternativas de símbolos y trabajar con Estados JustMyCode (vea el [Glosario del depurador de Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) para obtener una definición de "JustMyCode").

## <a name="notes-for-callers"></a>Notas para llamadores
 Una llamada a [getsymbolsearchinfo (](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) devuelve esta interfaz. El DE envía la interfaz [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) al administrador de depuración de la sesión (SDM) mediante el método de [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Además, una llamada a [QueryInterface](/cpp/atl/queryinterface) en una interfaz [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) devuelve esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de la interfaz [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Devuelve una lista de rutas de acceso en las que se buscan símbolos y los resultados de buscar en cada ruta.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carga e inicializa símbolos para el módulo actual.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Devuelve una marca que especifica si el módulo representa el código de usuario.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Especifica si el módulo se debe considerar o no código de usuario.|

## <a name="remarks"></a>Observaciones
 Visual Studio es el consumidor típico de esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
