---
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bebf232e17df54d4dae2392a40f2ccbc3fc711c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353311"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Proporciona compatibilidad para un proveedor de puerto seleccionar e interactuar con un servidor de núcleo.

## <a name="syntax"></a>Sintaxis

```
IDebugPortSupplierEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puerto personalizado implementa esta interfaz para que pueda seleccionar el servidor principal para usar.

## <a name="methods"></a>Métodos
 La tabla siguiente muestran los métodos de **IDebugPortSupplierEx2**.

|Método|Descripción|
|------------|-----------------|
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Establece el servidor principal para el proveedor del puerto.|

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)