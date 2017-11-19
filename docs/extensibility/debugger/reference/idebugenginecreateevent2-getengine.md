---
title: IDebugEngineCreateEvent2::GetEngine | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineCreateEvent2::GetEngine
helpviewer_keywords: IDebugEngineCreateEvent2::GetEngine
ms.assetid: 187d24ed-9f9a-4418-a0ef-b8a19f54652c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 665b3c66b91c87a15e541551b2b4a9ee2b562462
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugenginecreateevent2getengine"></a>IDebugEngineCreateEvent2::GetEngine
Recupera el objeto que representa el motor de depuración recién creado (Alemania).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetEngine(   
   IDebugEngine2** pEngine  
);  
```  
  
```csharp  
int GetEngine(   
   out IDebugEngine2 pEngine  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pEngine`  
 [out] Devuelve un [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objeto que representa el Alemania recién creado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)