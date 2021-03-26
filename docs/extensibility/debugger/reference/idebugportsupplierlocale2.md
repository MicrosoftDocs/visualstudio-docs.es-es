---
description: Proporciona compatibilidad con la configuración regional para un proveedor de puertos.
title: IDebugPortSupplierLocale2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: da7c08363d07e577d11259b8633aa15ac3cd0eb0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071771"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Proporciona compatibilidad con la configuración regional para un proveedor de puertos.

## <a name="syntax"></a>Sintaxis

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de Puerto personalizado implementa esta interfaz para establecer la configuración regional.

## <a name="methods"></a>Métodos
 En la tabla siguiente se muestran los métodos de **IDebugPortSupplierLocale2**.

|Método|Descripción|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Establece la configuración regional del proveedor del puerto.|

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
