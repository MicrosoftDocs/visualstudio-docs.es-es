---
title: IDebugEngine2::DestroyProgram | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::DestroyProgram
helpviewer_keywords: IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7efe7c8c4d917e6dd1868625ca1d80996176acb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informa a un motor de depuración (Alemania) que el programa especificado ha terminado atípicamente y que la DE debería limpiar todas las referencias al programa y evento de destrucción de un programa de envío.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pProgram`  
 [in] Un [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa el programa que ha finalizado atípicamente.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Una vez que se llama a este método, la DE posteriormente envía una [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) evento hacia el Administrador de sesión de depuración (SDM).  
  
 Este método no está implementado (devuelve `E_NOTIMPL`) si la DE se ejecuta en el mismo proceso que el programa que se está depurando. Este método se implementa sólo si la DE se ejecuta en el mismo proceso que el SDM.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)