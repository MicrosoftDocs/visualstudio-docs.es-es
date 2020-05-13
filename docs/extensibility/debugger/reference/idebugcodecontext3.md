---
title: IDebugCodeContext3 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3f81168d9af7fbbb93b5c59f3ab19a17107b56b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734188"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Extiende el [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz para habilitar la recuperación de interfaces de módulo y proceso.

## <a name="syntax"></a>Sintaxis

```
IDebugCodeContext3 : IDebugCodeContext2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implementado por motores de depuración [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] y consumido por el paquete de depuración.

## <a name="methods"></a>Métodos
 Además de los `IDebugCodeContext2` métodos de la interfaz, esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera una referencia a la interfaz del módulo de depuración.|
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera una referencia a la interfaz del proceso de depuración.|

## <a name="remarks"></a>Observaciones
 Esta es una interfaz opcional que generalmente no tiene que ser implementada.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
