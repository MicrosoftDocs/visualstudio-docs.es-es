---
description: Esta interfaz describe un puerto.
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 035b6364b3a1dea400c96bcf179d57d6b4808ad5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072226"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Esta interfaz describe un puerto. Esta descripción se usa para agregar el puerto a un proveedor de puerto.

## <a name="syntax"></a>Sintaxis

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Normalmente, Visual Studio implementa esta interfaz en el proceso de obtención de un puerto de depuración de un proveedor de puerto.

## <a name="notes-for-callers"></a>Notas para llamadores
 Esta interfaz se pasa a [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) para crear un puerto de depuración. Una llamada a [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) devuelve esta interfaz, que representa la solicitud utilizada para crear el puerto en primer lugar.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugPortRequest2` .

|Método|Descripción|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtiene el nombre del puerto que se va a crear.|

## <a name="remarks"></a>Observaciones
 Normalmente, un motor de depuración no interactúa con un proveedor de puerto y no tendrá ningún uso para esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
