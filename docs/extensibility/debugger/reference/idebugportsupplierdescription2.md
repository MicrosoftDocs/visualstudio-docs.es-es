---
description: Permite que la interfaz de usuario de Visual Studio muestre texto dentro de la sección información de transporte del cuadro de diálogo asociar al proceso.
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
ms.openlocfilehash: 8c3cd8d6fbeaf020ea772c9bd5cae783b6e8d127
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150385"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Permite [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] que la interfaz de usuario muestre texto dentro de la sección **información de transporte** del cuadro de diálogo **asociar al proceso** .

## <a name="syntax"></a>Syntax

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
