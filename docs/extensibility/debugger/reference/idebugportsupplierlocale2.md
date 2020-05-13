---
title: IDebugPortSupplierLocale2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98444ca60937d40262c92d89b8a6c48ed1a0b7ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724290"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Proporciona soporte de configuración regional para un proveedor de puertos.

## <a name="syntax"></a>Sintaxis

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puerto personalizado implementa esta interfaz para establecer la configuración regional.

## <a name="methods"></a>Métodos
 En la tabla siguiente se muestran los métodos de **IDebugPortSupplierLocale2**.

|Método|Descripción|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Establece la configuración regional para el proveedor de puertos.|

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
