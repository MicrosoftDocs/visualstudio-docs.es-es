---
title: IDebugProcess2::EnumThreads ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52383649fc45eae6bbac6831f9bb233b9c0a2fde
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724058"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Recupera una lista de todos los subprocesos que se ejecutan en el proceso.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
[fuera] Devuelve un [objeto IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) que contiene una lista de todos los subprocesos de todos los programas del proceso.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método enumera los subprocesos que se ejecutan en cada programa y, a continuación, los combina en una vista de proceso de los subprocesos. Un único subproceso puede ejecutarse en varios programas; este método enumera ese subproceso solo una vez.

 Este método presenta una lista de los subprocesos del proceso sin duplicados. De lo contrario, para enumerar los subprocesos que se ejecutan en un programa determinado, utilice el [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método.

## <a name="see-also"></a>Vea también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
