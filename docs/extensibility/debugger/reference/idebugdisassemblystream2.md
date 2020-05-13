---
title: IDebugDisassemblyStream2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ba08e4ec32aceaf6c265714848939cc6ad9c66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732049"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Esta interfaz representa una secuencia de instrucciones.

## <a name="syntax"></a>Sintaxis

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un motor de depuración implementa esta interfaz para admitir el desensamblado del código de un programa.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Una llamada al método [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) devuelve esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugDisassemblyStream2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[Lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lee las instrucciones a partir de la posición actual en la secuencia de desmontaje.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Mueve el puntero de lectura en la secuencia de desensamblado un número determinado de instrucciones con respecto a una posición especificada.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Devuelve un identificador de ubicación de código para un contexto de código determinado.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Devuelve un objeto de contexto de código correspondiente a un identificador de ubicación de código especificado.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Devuelve un identificador de ubicación de código que representa la ubicación de código actual.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtiene el documento de origen asociado a esta secuencia de desensamblado.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Obtiene el ámbito de esta secuencia de desensamblado.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtiene el tamaño de esta secuencia de desensamblado.|

## <a name="remarks"></a>Observaciones
 La secuencia de desensamblado se puede crear para representar todo el espacio de direcciones o simplemente una función o módulo dentro del espacio. Cada instrucción se representa mediante un [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura devuelta por una llamada a la [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
