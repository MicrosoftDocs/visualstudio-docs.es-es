---
title: IEnumDebugFrameInfo2::Reset | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2::Reset
helpviewer_keywords:
- IEnumDebugFrameInfo2::Reset
ms.assetid: e149b559-f072-480b-9552-a452b147f3a8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a73d89db4c821c78e75c37b44e961dcfbd7d189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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