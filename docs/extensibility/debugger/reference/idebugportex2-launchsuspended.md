---
title: "IDebugPortEx2::LaunchSuspended | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
helpviewer_keywords: 
  - "IDebugPortEx2::LaunchSuspended"
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Inicia un archivo ejecutable.  
  
## Sintaxis  
  
```cpp#  
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
  
```c#  
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
  
#### Parámetros  
 `pszExe`  
 \[in\]  El nombre del ejecutable que se arrancará.  Esto puede ser una ruta de acceso completa o relativa al directorio de trabajo especificado en el parámetro de `pszDir` .  
  
 `pszArgs`  
 \[in\]  Los argumentos que desee pasar a la aplicación ejecutable.  Puede ser un valor NULL si no hay ningún argumento.  
  
 `pszDir`  
 \[in\]  El nombre del directorio de trabajo utilizado por la aplicación ejecutable.  Puede ser un valor NULL si no se requiere ningún directorio de trabajo.  
  
 `bstrEnv`  
 \[in\]  Bloque de entorno de cadenas terminadas en null, seguido por un terminador adicional NULL.  
  
 `hStdInput`  
 \[in\]  identificador a un flujo de entrada alternativo.  puede ser 0 si la redirección no se requiere.  
  
 `hStdOutput`  
 \[in\]  Identificador de una secuencia de salida alternativa.  puede ser 0 si la redirección no se requiere.  
  
 `hStdError`  
 \[in\]  Identificador de una secuencia de salida de error alternativa.  puede ser 0 si la redirección no se requiere.  
  
 `ppPortProcess`  
 \[out\]  Devuelve un objeto de [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) que representa el proceso iniciará.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método debe iniciar el proceso suspenderlo y no ejecutando ningún código.  El método de [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) se llama para reanudar el proceso.  
  
 Un programa también se puede iniciar de un motor de depuración.  Para obtener información detallada, vea [Iniciar un programa](../../../extensibility/debugger/launching-a-program.md).  
  
## Vea también  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Iniciar un programa](../../../extensibility/debugger/launching-a-program.md)