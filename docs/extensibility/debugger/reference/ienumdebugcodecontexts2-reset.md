---
title: IEnumDebugCodeContexts2::Reset | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugCodeContexts2::Reset
helpviewer_keywords: IEnumDebugCodeContexts2::Reset
ms.assetid: df6cf1e3-2ef8-4d38-81a0-8e9adf151884
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bdefb66701e9b3f0a31657af3c3ce80cbdb1c295
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugcodecontexts2reset"></a>IEnumDebugCodeContexts2::Reset
Restablece la enumeración al primer elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Después de llamar a este método, la siguiente llamada a la [siguiente](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md) método devuelve el primer elemento de la enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)