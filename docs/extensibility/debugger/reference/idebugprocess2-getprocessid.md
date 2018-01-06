---
title: IDebugProcess2::GetProcessId | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::GetProcessId
helpviewer_keywords: IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5d11e954464b2e6d9fe892ab757781af078d2c27
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Obtiene el GUID de este proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```csharp  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pguidProcessId`  
 [out] Devuelve el GUID de este proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El identificador único global (GUID) identifica este proceso de todos los otros procesos que se ejecutan en el sistema.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)