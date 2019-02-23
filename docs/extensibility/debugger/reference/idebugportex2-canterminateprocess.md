---
title: IDebugPortEx2::CanTerminateProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12f8ad884045939c13f56e6a527643837be94d09
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685721"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Determina si se puede terminar un proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CanTerminateProcess( 
   IDebugProcess2* pPortProcess
);
```

```csharp
HRESULT CanTerminateProcess( 
   IDebugProcess2 pPortProcess
);
```

#### <a name="parameters"></a>Parámetros
 `pPortProcess`

 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso que se finalice.

## <a name="return-value"></a>Valor devuelto
 Devuelve `S_OK` si se puede finalizar el proceso; de lo contrario, devuelve `S_FALSE`.

## <a name="see-also"></a>Vea también
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)