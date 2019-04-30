---
title: IDebugBreakpointChecksumRequest2 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfad0d8469a3cd01b5697cd9ba74f7a84ee84b83
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923395"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
Representa una suma de comprobación de documento para una solicitud de punto de interrupción.

## <a name="syntax"></a>Sintaxis

```
IDebugBreakpointChecksumRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Implementada por el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurar paquete y utilizado por los motores de depuración.

## <a name="methods"></a>Métodos
 La tabla siguiente muestran los métodos de `IDebugBreakpointChecksumRequest2`.

|Método|Descripción|
|------------|-----------------|
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Recupera la suma de comprobación de documento para una solicitud de punto de interrupción según el identificador único del algoritmo de suma de comprobación para usar.|
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Determina si la suma de comprobación está habilitada para este documento.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll