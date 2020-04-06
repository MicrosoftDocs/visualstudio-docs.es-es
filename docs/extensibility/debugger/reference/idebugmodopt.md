---
title: IDebugModOpt ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt interface
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e142ed1229f59cfc22ff33cba48e9e35eb4e4406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726977"
---
# <a name="idebugmodopt"></a>IDebugModOpt
Representa un modificador opcional de depuración.

## <a name="syntax"></a>Sintaxis

```
IDebugModOpt : IUnknown
```

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Obtenido de un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa una clase o método.

## <a name="methods"></a>Métodos
 Esta interfaz implementa el siguiente método:

|Método|Descripción|
|------------|-----------------|
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Recupera una lista de modificadores opcionales.|

## <a name="requirements"></a>Requisitos
 Encabezado: Sh.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
