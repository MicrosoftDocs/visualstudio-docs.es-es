---
title: IDebugEngineLaunch2::LaunchSuspended ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730547"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Este método inicia un proceso mediante el motor de depuración (DE).

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT LaunchSuspended ( 
   LPCOLESTR             pszMachine,
   IDebugPort2*          pPort,
   LPCOLESTR             pszExe,
   LPCOLESTR             pszArgs,
   LPCOLESTR             pszDir,
   BSTR                  bstrEnv,
   LPCOLESTR             pszOptions,
   LAUNCH_FLAGS          dwLaunchFlags,
   DWORD                 hStdInput,
   DWORD                 hStdOutput,
   DWORD                 hStdError,
   IDebugEventCallback2* pCallback,
   IDebugProcess2**      ppDebugProcess
);
```

```csharp
int LaunchSuspended(
   string               pszServer,
   IDebugPort2          pPort,
   string               pszExe,
   string               pszArgs,
   string               pszDir,
   string               bstrEnv,
   string               pszOptions,
   enum_LAUNCH_FLAGS    dwLaunchFlags,
   uint                 hStdInput,
   uint                 hStdOutput,
   uint                 hStdError,
   IDebugEventCallback2 pCallback,
   out IDebugProcess2   ppProcess
);
```

## <a name="parameters"></a>Parámetros
`pszMachine`\
[en] El nombre de la máquina en la que se iniciará el proceso. Utilice un valor nulo para especificar el equipo local.

`pPort`\
[en] El [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz que representa el puerto que se ejecutará el programa en.

`pszExe`\
[en] El nombre del ejecutable que se va a iniciar.

`pszArgs`\
[en] Los argumentos que se pasan al ejecutable. Puede ser un valor nulo si no hay argumentos.

`pszDir`\
[en] El nombre del directorio de trabajo utilizado por el ejecutable. Puede ser un valor nulo si no se requiere ningún directorio de trabajo.

`bstrEnv`\
[en] Bloque de entorno de cadenas terminadas en NULL, seguido de un terminador NULL adicional.

`pszOptions`\
[en] Las opciones para el ejecutable.

`dwLaunchFlags`\
[en] Especifica el [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) de una sesión.

`hStdInput`\
[en] Controle una secuencia de entrada alternativa. Puede ser 0 si no se requiere la redirección.

`hStdOutput`\
[en] Controle una secuencia de salida alternativa. Puede ser 0 si no se requiere la redirección.

`hStdError`\
[en] Controle una secuencia de salida de error alternativa. Puede ser 0 si no se requiere la redirección.

`pCallback`\
[en] El objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que recibe eventos del depurador.

`ppDebugProcess`\
[fuera] Devuelve el resultante [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso iniciado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Normalmente, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] inicia un programa mediante el método [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) y, a continuación, adjunta el depurador al programa suspendido. Sin embargo, hay circunstancias en las que el motor de depuración puede necesitar iniciar un programa (por ejemplo, si el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] motor `IDebugEngineLaunch2::LaunchSuspended` de depuración forma parte de un intérprete y el programa que se está depurando es un lenguaje interpretado), en cuyo caso utiliza el método.

 Se llama al método [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) para iniciar el proceso después de que el proceso se haya iniciado correctamente en un estado suspendido.

## <a name="see-also"></a>Vea también
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
