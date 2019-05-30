---
title: IDebugProcessQueryProperties | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ddb98c2d7e63fc27ad1469dfbfc76eaaee38582
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353110"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Esta interfaz es una interfaz de extensión implementada por [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) los implementadores. Permite que el implementador obtener información sobre el entorno de proceso de depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implemente esta interfaz para obtener información sobre el entorno de ejecución de un proceso de depuración.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugProcessQueryProperties`.

|Método|Descripción|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Consultas para un valor de propiedad.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Consultas para los valores de propiedad.|

## <a name="remarks"></a>Comentarios
 Rara vez se implementa esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)