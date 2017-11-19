---
title: IDebugPortEx2::TerminateProcess | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2::TerminateProcess
helpviewer_keywords: IDebugPortEx2::TerminateProcess
ms.assetid: bf8fa94c-6d9d-4e4f-ac08-3b44ba5ace68
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4863c9c810c4986efea4c87c37460a80ad5e943
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportex2terminateprocess"></a>IDebugPortEx2::TerminateProcess
Termina un proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT TerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```csharp  
int TerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pPortProcess`  
 [in] Un [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa el proceso haya finalizado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)