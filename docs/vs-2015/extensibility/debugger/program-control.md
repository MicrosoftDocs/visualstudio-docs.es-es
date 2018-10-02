---
title: Control del programa | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b213ee6eca5d132c663e86d6829b688952d150d4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575263"
---
# <a name="program-control"></a>Control de programas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Control del programa](https://docs.microsoft.com/visualstudio/extensibility/debugger/program-control).  
  
En Visual Studio depurando, todos de la versión siguiente y continuar rutinas se producen en el nivel de programa:  
  
-   Establecer la instrucción siguiente, es decir, si se establece el equipo en la siguiente instrucción que se ejecuta en un entorno de marco determinado  
  
-   Es decir, ejecutar, continúe salir del modo de ejecución paso a paso  
  
-   Ejecución paso a paso a la siguiente instrucción  
  
-   Continuando con el modo de ejecución paso a paso actual  
  
-   Suspender los subprocesos contenidos en el programa  
  
-   Reanudar los subprocesos contenidos en el programa  
  
> [!NOTE]
>  Ver la pila de llamadas se implementa en el nivel de subproceso. Para enumerar la información de marco al ver la pila de llamadas para un subproceso, debe implementar todos los métodos de la [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaz.  
  
## <a name="methods-of-program-control"></a>Métodos de Control del programa  
 La tabla siguiente muestran los métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que debe implementarse para un motor de depuración mínimamente funcional (DE) y el control de ejecución.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continúa ejecutándose en todos los subprocesos contenidos en un programa desde un estado detenido. Se requiere para el control de ejecución.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continúa ejecutándose en todos los subprocesos contenidos en un programa desde un estado detenido. Se requiere para el control de ejecución.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza un paso en el subproceso especificado. Continúa ejecutándose en todos los demás subprocesos contenidos en el programa. Se requiere para el control de ejecución.|  
  
 Los programas multiproceso, también debe implementar la [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método y todos los métodos de la [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)

