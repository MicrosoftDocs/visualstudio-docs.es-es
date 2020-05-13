---
title: IEnumDebugPorts2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3cc46ef8abb6ef1fbb8f072d97b0fc4a537af1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716101"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Esta interfaz enumera los puertos de una máquina o proveedor de puertos.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puertos personalizado implementa esta interfaz para representar una lista de puertos creados por el proveedor. Visual Studio implementa esta interfaz en compatibilidad con su propio proveedor de puertos.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) para obtener esta interfaz que representa una lista de puertos creados por el proveedor de puertos. Llame a [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) para obtener esta interfaz que representa una lista de puertos que se guardaron en el disco.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IEnumDebugPorts2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Recupera un número especificado de puertos en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Omite un número especificado de puertos en una secuencia de enumeración.|
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Obtiene el número de puertos de un enumerador.|

## <a name="remarks"></a>Observaciones
 Visual Studio usa esta interfaz para ayudar a rellenar una lista de puertos utilizados para adjuntar a procesos.

 Un motor de depuración normalmente no utiliza esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
