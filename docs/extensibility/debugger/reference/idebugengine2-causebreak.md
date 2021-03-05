---
description: Solicita que todos los programas depurados por este motor DE depuración (DE) detengan la ejecución la próxima vez que uno de los subprocesos intente ejecutarse.
title: 'IDebugEngine2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 344ca2e9e9758aaca5a2c1e6784a36467abde73c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162711"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Solicita que todos los programas depurados por este motor DE depuración (DE) detengan la ejecución la próxima vez que uno de los subprocesos intente ejecutarse.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método es asincrónico: se envía un evento [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) cuando el programa siguiente intenta ejecutarse después de llamar a este método.

## <a name="see-also"></a>Consulte también
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
