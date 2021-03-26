---
description: Representa un modificador opcional Debug.
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffb235d58c254d130636da0f4b97961c11f9a372
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087904"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Representa un modificador opcional Debug.

## <a name="syntax"></a>Sintaxis

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Notas para llamadores
 Se obtiene a partir de un objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa una clase o un método.

## <a name="methods"></a>Métodos
 Esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera una lista de modificadores opcionales.|

## <a name="requirements"></a>Requisitos
 Encabezado: SH. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
