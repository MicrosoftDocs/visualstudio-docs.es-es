---
title: "IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::LaunchSuspended"
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método inicia un proceso mediante el motor de depuración \(DE\).  
  
## Sintaxis  
  
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
  
```c#  
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
  
#### Parámetros  
 `pszMachine`  
 \[in\]  El nombre del equipo donde para iniciar el proceso.  Utilice un valor null para especificar el equipo local.  
  
 `pPort`  
 \[in\]  La interfaz de [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) que representa el puerto que el programa ejecutará.  
  
 `pszExe`  
 \[in\]  El nombre del ejecutable que se arrancará.  
  
 `pszArgs`  
 \[in\]  Los argumentos que desee pasar a la aplicación ejecutable.  Puede ser un valor NULL si no hay ningún argumento.  
  
 `pszDir`  
 \[in\]  El nombre del directorio de trabajo utilizado por la aplicación ejecutable.  Puede ser un valor NULL si no se requiere ningún directorio de trabajo.  
  
 `bstrEnv`  
 \[in\]  Bloque de entorno de cadenas terminadas en null, seguido por un terminador adicional NULL.  
  
 `pszOptions`  
 \[in\]  Las opciones para el ejecutable.  
  
 `dwLaunchFlags`  
 \[in\]  especifica [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) para una sesión.  
  
 `hStdInput`  
 \[in\]  identificador a un flujo de entrada alternativo.  puede ser 0 si la redirección no se requiere.  
  
 `hStdOutput`  
 \[in\]  Identificador de una secuencia de salida alternativa.  puede ser 0 si la redirección no se requiere.  
  
 `hStdError`  
 \[in\]  Identificador de una secuencia de salida de error alternativa.  puede ser 0 si la redirección no se requiere.  
  
 `pCallback`  
 \[in\]  El objeto de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que recibe eventos de depurador.  
  
 `ppDebugProcess`  
 \[out\]  Devuelve el objeto resultante de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa el proceso iniciará.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Normalmente, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] inicia un programa mediante el método de [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) y después asocia el depurador al programa suspendido.  Sin embargo, hay circunstancias en las que el motor de depuración puede necesitar iniciar un programa \(por ejemplo, si es parte el motor de depuración de un intérprete y el programa que se están depurando es un lenguaje interpreta\), en este caso [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] utiliza el método de `IDebugEngineLaunch2::LaunchSuspended` .  
  
 El método de [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) se llama para iniciar el proceso después de que el proceso se haya iniciará correctamente en un estado suspendido.  
  
## Vea también  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH\_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)