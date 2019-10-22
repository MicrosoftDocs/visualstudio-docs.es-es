---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94810761e546b0cae9eca32fc76bc0bfd396c7e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311117"
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
[in] El nombre del archivo ejecutable que se iniciará. Esto puede ser una ruta de acceso completa o relativa al directorio de trabajo especificado en el `pszDir` parámetro.

`pszArgs`\
[in] Los argumentos para pasar al ejecutable. Puede ser un valor null si no hay ningún argumento.

`pszDir`\
[in] El nombre del directorio de trabajo usando el archivo ejecutable. Puede ser un valor null si no se requiere ningún directorio de trabajo.

`bstrEnv`\
[in] Bloque de entorno de cadenas terminadas en null, seguido de un terminador NULL adicional.

`hStdInput`\
[in] Identificador de un flujo de entrada alternativo. Puede ser 0 si no se requiere la redirección.

`hStdOutput`\
[in] Identificador de un flujo de salida alternativos. Puede ser 0 si no se requiere la redirección.

`hStdError`\
[in] Identificador de un flujo de salida de error alternativa. Puede ser 0 si no se requiere la redirección.

`ppPortProcess`\
[out] Devuelve un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa el proceso iniciado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método debería iniciar el proceso, por lo que TI está suspendida y no se está ejecutando ningún código. El [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) método se llama para reanudar el proceso.

 También se puede iniciar un programa desde un motor de depuración. Para obtener más información, consulte [iniciar un programa](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Vea también
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Inicio de un programa](../../../extensibility/debugger/launching-a-program.md)