---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62be3ce13ecbc3180cf2bbcce26b04f3d79edb1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731155"
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

## <a name="see-also"></a>Vea también
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
