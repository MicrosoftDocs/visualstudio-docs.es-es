---
title: "IDebugProgram3::ExecuteOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3::ExecuteOnThread"
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ejecuta el programa del depurador.  El subproceso se devuelve del depurador la información en la que el subproceso el usuario está viendo al ejecutar el programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```c#  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### Parámetros  
 `pThread`  
 \[in\]  un objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 hay tres maneras diferentes que un depurador puede reanudar la ejecución después de detener:  
  
-   Execute: Cancelar cualquier paso anterior, y ejecute hasta el punto de interrupción siguiente y así sucesivamente.  
  
-   paso: Cancelar cualquier anterior paso, y ejecute hasta el nuevo paso completa.  
  
-   continúe: Ejecute de nuevo, y permite cualquier activo anterior del paso.  
  
 El último subproceso a `ExecuteOnThread` es útil al decidir qué paso a la cancelación.  Si no conoce el subproceso, ejecución ejecuta las cancela todos los pasos.  Con el conocimiento del subproceso, sólo necesita cancelar el paso en el subproceso activo.  
  
## Vea también  
 [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)