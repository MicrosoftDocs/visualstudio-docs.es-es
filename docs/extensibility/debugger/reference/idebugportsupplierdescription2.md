---
title: IDebugPortSupplierDescription2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724356"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Permite [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] que la interfaz de usuario muestre texto dentro de la sección Información de **transporte** del cuadro de diálogo **Adjuntar al proceso.**

## <a name="syntax"></a>Sintaxis

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz es implementada por los proveedores de puertos.

## <a name="methods"></a>Métodos
 En la tabla siguiente `IDebugPortSupplierDescription2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera los metadatos de descripción y descripción del proveedor de puertos.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
