---
title: IDebugObject2::GetAlias | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::GetAlias
helpviewer_keywords: IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a487043d6c046a9c117c4845d56db2f18bf51896
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Obtiene el alias asociado a este objeto, si existe.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppAlias`  
 [out] Devuelve un [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) el objeto que representa el alias para este objeto; en caso contrario, devuelve un valor null.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se crea un alias para un objeto con una llamada a la [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)