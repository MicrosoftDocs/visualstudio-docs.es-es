---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2b78986b997358d7f15c9c8c73bb4bd0f73aaf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695432"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Esta interfaz describe un puerto. Esta descripción se utiliza para agregar el puerto a un proveedor de puerto.

## <a name="syntax"></a>Sintaxis

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio normalmente implementa esta interfaz en el proceso de obtención de un puerto de depuración de un proveedor de puerto.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Esta interfaz se pasa a [agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) para crear un puerto de depuración. Una llamada a [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) devuelve esta interfaz, que representa la solicitud utilizada para crear el puerto en primer lugar.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugPortRequest2`.

|Método|Descripción|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtiene el nombre del puerto que se va a crear.|

## <a name="remarks"></a>Comentarios
 Normalmente, un motor de depuración no interactúa con un proveedor de puerto y no tendrá ningún uso para esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)