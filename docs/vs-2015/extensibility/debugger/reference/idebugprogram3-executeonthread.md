---
title: IDebugProgram3::ExecuteOnThread | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e183d9d55c8527cdead0d7108c12ac3fd527e94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788633"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ejecuta el programa de depurador. El subproceso se devuelve para proporcionar la información del depurador en el subproceso que el usuario está viendo cuando se ejecuta el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Hay tres maneras diferentes que puede reanudar la ejecución después de detener un depurador:  
  
- Ejecute: Cancelar cualquier paso anterior y ejecutar hasta el siguiente punto de interrupción y así sucesivamente.  
  
- Paso: Cancelar un paso anterior y ejecutar hasta que se complete el paso nuevo.  
  
- Continuar: Vuelva a ejecutar y dejar activa la cualquier paso anterior.  
  
  El subproceso pasa a `ExecuteOnThread` es útil al decidir qué paso para cancelar. Si no conoce el subproceso, que se ejecuta ejecutar cancela todos los pasos. Con el conocimiento del subproceso, solo deberá cancelar el paso en el subproceso activo.  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)

