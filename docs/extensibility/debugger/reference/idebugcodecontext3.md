---
description: Extiende la interfaz IDebugCodeContext2 para habilitar la recuperación de interfaces de módulo y de proceso.
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db806a4b45e855533e4ded1419f2d2117fb4f912
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164024"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Extiende la interfaz [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) para habilitar la recuperación de interfaces de módulo y de proceso.

## <a name="syntax"></a>Syntax

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implementado por los motores de depuración y consumido por el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] paquete de depuración.

## <a name="methods"></a>Métodos
 Además de los métodos de la `IDebugCodeContext2` interfaz, esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera una referencia a la interfaz del módulo de depuración.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera una referencia a la interfaz del proceso de depuración.|

## <a name="remarks"></a>Observaciones
 Se trata de una interfaz opcional que, por lo general, no tiene que implementarse.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
