---
title: IEnumDebugFrameInfo2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716612"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Esta interfaz enumera las estructuras [FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

## <a name="syntax"></a>Sintaxis

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para proporcionar una lista de estructuras que describe la pila de llamadas actual.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Visual Studio llama a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obtener esta interfaz cada vez que se produce un punto de interrupción, una excepción o una detención en un programa que se está depurando.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IEnumDebugFrameInfo2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Recupera un número especificado de [estructuras FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Omite un número especificado de [estructuras FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) en una secuencia de enumeración.|
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Obtiene el número de estructuras [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) en un enumerador.|

## <a name="remarks"></a>Observaciones
 Visual Studio obtiene esta interfaz como el primer paso para controlar un punto de interrupción, una excepción o una pausa generada por el usuario en el programa que se está depurando. La lista de estructuras [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) representa la pila de llamadas actual, con la llamada de función actual al principio de la lista y la llamada de función más antigua al final de la lista. Cada `FRAMEINFO` uno representa un marco de pila, un contexto en el que se pueden evaluar expresiones y examinar variables locales.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
