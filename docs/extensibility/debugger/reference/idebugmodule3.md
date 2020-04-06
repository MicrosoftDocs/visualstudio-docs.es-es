---
title: IDebugModule3 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726736"
---
# <a name="idebugmodule3"></a>IDebugModule3
Esta interfaz representa un módulo que admite ubicaciones alternativas de símbolos y estados JustMyCode.

## <a name="syntax"></a>Sintaxis

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para admitir ubicaciones alternativas de símbolos y para trabajar con estados JustMyCode (consulte el [glosario](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) del depurador de Visual Studio para obtener una definición de "JustMyCode").

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Una llamada a [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) devuelve esta interfaz. El DE envía el [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) interfaz al administrador de depuración de sesión (SDM) mediante el [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método. Además, una llamada a [QueryInterface](/cpp/atl/queryinterface) en un [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interfaz devuelve esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de la [interfaz IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Devuelve una lista de rutas buscadas de símbolos y los resultados de buscar en cada ruta de acceso.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carga e inicializa símbolos para el módulo actual.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Devuelve flag especificando si el módulo representa el código de usuario.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Especifica si el módulo debe considerarse código de usuario o no.|

## <a name="remarks"></a>Observaciones
 Visual Studio es el consumidor típico de esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
