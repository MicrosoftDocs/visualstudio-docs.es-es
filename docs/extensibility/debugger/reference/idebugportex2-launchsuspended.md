---
title: IDebugPortEx2::LaunchSuspended ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725101"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Inicia un archivo ejecutable.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Parámetros
`pszExe`\
[en] El nombre del ejecutable que se va a iniciar. Puede ser una ruta de acceso completa o `pszDir` relativa al directorio de trabajo especificado en el parámetro.

`pszArgs`\
[en] Los argumentos que se pasan al ejecutable. Puede ser un valor nulo si no hay argumentos.

`pszDir`\
[en] El nombre del directorio de trabajo utilizado por el ejecutable. Puede ser un valor nulo si no se requiere ningún directorio de trabajo.

`bstrEnv`\
[en] Bloque de entorno de cadenas terminadas en null, seguido de un terminador NULL adicional.

`hStdInput`\
[en] Controle una secuencia de entrada alternativa. Puede ser 0 si no se requiere la redirección.

`hStdOutput`\
[en] Controle una secuencia de salida alternativa. Puede ser 0 si no se requiere la redirección.

`hStdError`\
[en] Controle una secuencia de salida de error alternativa. Puede ser 0 si no se requiere la redirección.

`ppPortProcess`\
[fuera] Devuelve un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa el proceso iniciado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método debe iniciar el proceso para que se suspenda y no ejecute ningún código. El [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) se llama al método para reanudar el proceso.

 Un programa también se puede iniciar desde un motor de depuración. Para obtener más información, consulte [Lanzamiento de un programa](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Vea también
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Inicio de un programa](../../../extensibility/debugger/launching-a-program.md)
