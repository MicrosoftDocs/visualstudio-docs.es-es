---
title: IDebugPrimitiveTypeField ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07cd3d1a1f80d1c5e816877b7e70a9e65d24d650
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724273"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Representa un valor de enumeración de tipo primitivo de un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz.

## <a name="syntax"></a>Sintaxis

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Métodos
 Además de los métodos de la [interfaz IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Recupera el tipo primitivo asociado a este campo.|

## <a name="requirements"></a>Requisitos
 Encabezado: Sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
