---
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4012b919cffc5e16433567fac283ac731d4d215c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353278"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Representa un valor de enumeración de tipo primitivo de una [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz.

## <a name="syntax"></a>Sintaxis

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Métodos
 Además de los métodos en el [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaz, esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Recupera el tipo primitivo asociado a este campo.|

## <a name="requirements"></a>Requisitos
 Encabezado: Sh.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll