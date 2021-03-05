---
description: Representa un modificador opcional Debug.
title: IDebugModOpt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 047c01f78931e1b13110640952c67c11a68bc8a2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149865"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Representa un modificador opcional Debug.

## <a name="syntax"></a>Syntax

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
