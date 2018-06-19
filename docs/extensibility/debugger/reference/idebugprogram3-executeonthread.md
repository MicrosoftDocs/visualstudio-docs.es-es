---
title: IDebugProgram3::ExecuteOnThread | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8aff643014da16ed9644573a77cb8444836d713d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117067"
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