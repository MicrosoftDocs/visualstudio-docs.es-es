---
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3db59d4938911d0c47f0122a8727be8f1c8acd67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840202"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Permite [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] que la interfaz de usuario muestre texto dentro de la sección **información de transporte** del cuadro de diálogo **asociar al proceso** .

## <a name="syntax"></a>Sintaxis

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz la implementan los proveedores de puertos.

## <a name="methods"></a>Métodos
 En la tabla siguiente se muestran los métodos de `IDebugPortSupplierDescription2` .

|Método|Descripción|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera los metadatos de Descripción y descripción para el proveedor del puerto.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
