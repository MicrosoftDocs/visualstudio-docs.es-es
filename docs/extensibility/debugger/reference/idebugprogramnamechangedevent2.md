---
title: IDebugProgramNameChangedEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramNameChangedEvent2 interface
ms.assetid: be1f1cd5-0b2f-435c-a052-dca28a7c978d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0640fa06b821c6679bc52c9f92a757cee6f0a580
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898740"
---
# <a name="idebugprogramnamechangedevent2"></a>IDebugProgramNameChangedEvent2
Se envía desde el motor de depuración (DE) al administrador de depuración de la sesión (SDM) cuando cambia el nombre de un programa.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramNameChangedEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El DE implementa esta interfaz para notificar que el nombre del programa ha cambiado. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la interfaz **IDebugEvent2** .

## <a name="notes-for-callers"></a>Notas para llamadores
 Crea y envía este objeto DE evento para notificar un cambio de nombre de programa. El DE envía este evento mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando. El proveedor del puerto personalizado envía este evento mediante la interfaz I.

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
