---
title: IDebugProgram3::ExecuteOnThread | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 649b16c1b57b2f66772c2117b776e6b79ad862be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Ejecuta el programa de depurador. El subproceso se devuelve para proporcionar a la información del depurador de subproceso en el que está viendo el usuario al ejecutar el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pThread`  
 [in] Un [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Hay tres maneras diferentes que puede reanudar la ejecución después de detener un depurador:  
  
-   Ejecutar: Cancelar un paso anterior y ejecutar hasta el punto de interrupción siguiente y así sucesivamente.  
  
-   Paso: Cancelar un paso anterior y ejecutar hasta que se completa el paso nuevo.  
  
-   Continuar: Vuelva a ejecutar y dejar activa la cualquier paso anterior.  
  
 El subproceso pasa a `ExecuteOnThread` es útil al decidir qué paso para cancelar. Si no conoce el subproceso en el que se ejecuta ejecutar cancela todos los pasos. Con el conocimiento del subproceso, sólo necesita cancelar el paso en el subproceso activo.  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)