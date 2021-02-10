---
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae588724f19f9722244ce69f77b64fad07552f9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938179"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Esta interfaz es una interfaz de extensión implementada por implementadores de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) . Permite al implementador obtener información sobre el entorno de proceso de depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implemente esta interfaz para obtener información sobre el entorno de ejecución de un proceso de depuración.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugProcessQueryProperties` .

|Método|Descripción|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Consulta un valor de propiedad.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Consulta los valores de propiedad.|

## <a name="remarks"></a>Notas
 Rara vez se implementa esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
