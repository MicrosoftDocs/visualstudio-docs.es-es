---
description: Permite que la interfaz de usuario de Visual Studio muestre texto dentro de la sección información de transporte del cuadro de diálogo asociar al proceso.
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dba3cd07bb84843ff4d2531cdde63ab9e671f961
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071927"
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
