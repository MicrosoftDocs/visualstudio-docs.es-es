---
title: 'IDebugEngineLaunch2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08f59f9f099f4cec52760c8a8364feb8f5481ffa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195746"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método inicia un proceso por medio del motor de depuración (DE).  
  
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
 de Nombre del equipo en el que se va a iniciar el proceso. Use un valor null para especificar el equipo local.  
  
 `pPort`  
 de La interfaz [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa el puerto en el que se ejecutará el programa.  
  
 `pszExe`  
 de Nombre del ejecutable que se va a iniciar.  
  
 `pszArgs`  
 de Argumentos que se van a pasar al archivo ejecutable. Puede ser un valor NULL si no hay ningún argumento.  
  
 `pszDir`  
 de Nombre del directorio de trabajo utilizado por el ejecutable. Puede ser un valor NULL si no se requiere ningún directorio de trabajo.  
  
 `bstrEnv`  
 de Bloque de entorno de cadenas terminadas en NULL, seguido de un terminador NULL adicional.  
  
 `pszOptions`  
 de Opciones del archivo ejecutable.  
  
 `dwLaunchFlags`  
 de Especifica el [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) para una sesión.  
  
 `hStdInput`  
 de Identificador de un flujo de entrada alternativo. Puede ser 0 si no se requiere redirección.  
  
 `hStdOutput`  
 de Identificador de un flujo de salida alternativo. Puede ser 0 si no se requiere redirección.  
  
 `hStdError`  
 de Identificador de un flujo de salida de error alternativo. Puede ser 0 si no se requiere redirección.  
  
 `pCallback`  
 de El objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que recibe eventos del depurador.  
  
 `ppDebugProcess`  
 enuncia Devuelve el objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) resultante que representa el proceso iniciado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 Normalmente, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] inicia un programa con el método [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) y, a continuación, asocia el depurador al programa suspendido. Sin embargo, hay circunstancias en las que el motor de depuración puede necesitar iniciar un programa (por ejemplo, si el motor de depuración forma parte de un intérprete y el programa que se está depurando es un lenguaje interpretado), en cuyo caso [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] usa el `IDebugEngineLaunch2::LaunchSuspended` método.  
  
 Se llama al método [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) para iniciar el proceso una vez que el proceso se ha iniciado correctamente en un estado suspendido.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
