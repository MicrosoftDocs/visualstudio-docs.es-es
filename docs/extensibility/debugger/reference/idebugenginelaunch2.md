---
title: "IDebugEngineLaunch2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2"
helpviewer_keywords: 
  - "Interfaz IDebugEngineLaunch2"
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Utiliza un motor de depuración \(DE\) para iniciar y finalizar programas.  
  
## Sintaxis  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa mediante una personalizada OF si tiene requisitos especiales para iniciar un proceso que no se pueda controlar completamente mediante un puerto personalizado.  Suele ser el caso cuando el OF es parte de un intérprete y el proceso que se está depurando es un script: el intérprete necesita ser iniciará primero, y el script se carga y iniciado.  Un puerto puede iniciar el intérprete, pero el script puede requerir tratamiento especial \(que es donde el OF tiene un rol\).  Se implementa esta interfaz únicamente si hay requisitos únicos para iniciar un programa que un puerto personalizado no pueda controlar.  
  
## Notas para los llamadores  
 Esta interfaz es denominada por el administrador de depuración de la sesión \(SDM\) si el SDM puede obtener esta interfaz de la interfaz de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) \(mediante QueryInterface\).  Si esta interfaz puede obtenerse, el SDM sabe que el OF tiene requisitos especiales y llama a esta interfaz para iniciar el programa en lugar de iniciar el puerto él.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugEngineLaunch2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Inicia un proceso mediante el OF.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Reanuda la ejecución de procesos.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina si el proceso puede ser finalizado.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termina un proceso.|  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)