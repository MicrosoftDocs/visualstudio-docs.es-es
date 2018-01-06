---
title: IDebugProgram2::Terminate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Terminate
helpviewer_keywords: IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fea9b99fc597a75e93392b14fe40a1be87072602
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Finaliza el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si es posible, el programa se termina y descargando desde el proceso; en caso contrario, el motor de depuración (Alemania) llevará a cabo cualquier limpieza necesaria.  
  
 Este método o el [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) el IDE, normalmente en respuesta al usuario detener la depuración de todos los llama el método. La implementación de este método lo ideal es que, debería, finalizar el programa dentro del proceso. Si esto no es posible, el DE debe impedir que el programa se ejecuten más en este proceso (y realizar cualquier limpieza necesaria). Si el `IDebugProcess2::Terminate` método se llamó por el IDE, se terminará el proceso completo algún tiempo después del `IDebugProgram2::Terminate` se llama al método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Finalizar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)