---
title: IDebugEngine3::SetEngineGuid | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::SetEngineGuid
helpviewer_keywords: IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f31bc27cdfe197a118d1b696225ea332fc0026ca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
Este método establece el motor de depuración (Alemania) `GUID`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetEngineGuid(  
   GUID* guidEngine  
);  
```  
  
```  
[C#]  
int SetEngineGuid(  
   ref Guid guidEngine  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidEngine`  
 [in] `GUID` del motor.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)