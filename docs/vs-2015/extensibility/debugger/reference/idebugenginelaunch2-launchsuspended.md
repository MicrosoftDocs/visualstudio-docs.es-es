---
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8fe234359d864f5df3ae568b8f3ec0c55c0ee9ff
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580474"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugEngineLaunch2::LaunchSuspended](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugenginelaunch2-launchsuspended).  
  
Este método inicia un proceso mediante el motor de depuración (DE).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parámetros  
 `pszMachine`  
 [in] El nombre de la máquina en que se va a iniciar el proceso. Use un valor null para especificar el equipo local.  
  
 `pPort`  
 [in] El [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz que representa el puerto que se ejecutará el programa.  
  
 `pszExe`  
 [in] El nombre del archivo ejecutable que se iniciará.  
  
 `pszArgs`  
 [in] Los argumentos para pasar al ejecutable. Puede ser un valor null si no hay ningún argumento.  
  
 `pszDir`  
 [in] El nombre del directorio de trabajo usando el archivo ejecutable. Puede ser un valor null si no se requiere ningún directorio de trabajo.  
  
 `bstrEnv`  
 [in] Bloque de entorno de cadenas terminadas en NULL, seguido de un terminador NULL adicional.  
  
 `pszOptions`  
 [in] Las opciones para el archivo ejecutable.  
  
 `dwLaunchFlags`  
 [in] Especifica el [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) para una sesión.  
  
 `hStdInput`  
 [in] Identificador de un flujo de entrada alternativo. Puede ser 0 si no se requiere la redirección.  
  
 `hStdOutput`  
 [in] Identificador de un flujo de salida alternativos. Puede ser 0 si no se requiere la redirección.  
  
 `hStdError`  
 [in] Identificador de un flujo de salida de error alternativa. Puede ser 0 si no se requiere la redirección.  
  
 `pCallback`  
 [in] El [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que recibe los eventos del depurador.  
  
 `ppDebugProcess`  
 [out] Devuelve el resultado [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso iniciado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] inicia un programa mediante la [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) método y, a continuación, asocia el depurador al programa suspendido. Sin embargo, hay circunstancias en que el motor de depuración es posible que deba iniciar un programa (por ejemplo, si el motor de depuración es parte de un intérprete y el programa que se está depurando es un lenguaje interpretado), en cuyo caso [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] usa el `IDebugEngineLaunch2::LaunchSuspended` (método) .  
  
 El [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) método se llama para iniciar el proceso después de iniciar el proceso en un estado suspendido.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)

