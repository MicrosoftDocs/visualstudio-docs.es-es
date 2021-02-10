---
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
ms.openlocfilehash: 0aff72199b6b79f2cca30e99533311ac617816b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941780"
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
