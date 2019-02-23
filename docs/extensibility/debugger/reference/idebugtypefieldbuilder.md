---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 456fe2656949e0cc862acdb97149b85f037beac8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720121"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Representa la capacidad para crear un campo que representa un tipo.

## <a name="syntax"></a>Sintaxis

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Notas para los llamadores
 Esta interfaz se obtiene desde el proveedor de símbolos.

## <a name="methods"></a>Métodos
 Esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Crea un objeto que representa un tipo primitivo.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Crea un puntero al tipo especificado.|

## <a name="requirements"></a>Requisitos
 Encabezado: Sh.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll