---
title: IEnumDebugFrameInfo2::Reset | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFrameInfo2::Reset
helpviewer_keywords: IEnumDebugFrameInfo2::Reset
ms.assetid: e149b559-f072-480b-9552-a452b147f3a8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 34aceab3b4abfd431e0d264a6cd82af5f611e869
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugframeinfo2reset"></a>IEnumDebugFrameInfo2::Reset
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
 Después de llamar a este método, la siguiente llamada a la [siguiente](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) método devuelve el primer elemento de la enumeración.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)