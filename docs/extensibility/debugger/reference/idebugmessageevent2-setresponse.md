---
title: IDebugMessageEvent2::SetResponse | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6dfb3c71b15e54a622523833f58706d24b61484d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
Establece la respuesta, si existe, en el cuadro de mensaje.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetResponse(   
   DWORD dwResponse  
);  
```  
  
```csharp  
int SetResponse(   
   uint dwResponse  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwResponse`  
 [in] Especifica la respuesta, usando las convenciones de Win32 `MessageBox` función. Consulte la [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) función para obtener más información.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)