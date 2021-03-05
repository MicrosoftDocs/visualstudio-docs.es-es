---
description: Inicia un archivo ejecutable.
title: 'IDebugPortEx2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5982ad665333aa4d11e2098d3b148db88e77c32
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142834"
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
de Nombre del ejecutable que se va a iniciar. Puede ser una ruta de acceso completa o relativa al directorio de trabajo especificado en el `pszDir` parámetro.

`pszArgs`\
de Argumentos que se van a pasar al archivo ejecutable. Puede ser un valor NULL si no hay ningún argumento.

`pszDir`\
de Nombre del directorio de trabajo utilizado por el ejecutable. Puede ser un valor NULL si no se requiere ningún directorio de trabajo.

`bstrEnv`\
de Bloque de entorno de cadenas terminadas en null, seguido de un terminador NULL adicional.

`hStdInput`\
de Identificador de un flujo de entrada alternativo. Puede ser 0 si no se requiere redirección.

`hStdOutput`\
de Identificador de un flujo de salida alternativo. Puede ser 0 si no se requiere redirección.

`hStdError`\
de Identificador de un flujo de salida de error alternativo. Puede ser 0 si no se requiere redirección.

`ppPortProcess`\
enuncia Devuelve un objeto [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) que representa el proceso iniciado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Este método debe iniciar el proceso para que se suspenda y no se ejecute ningún código. Se llama al método [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) para reanudar el proceso.

 Un programa también se puede iniciar desde un motor de depuración. Para obtener más información, vea [iniciar un programa](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Consulte también
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Inicio de un programa](../../../extensibility/debugger/launching-a-program.md)
