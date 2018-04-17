---
title: IDebugIDECallback::DisplayMessage | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04727fc05de87181195aae2afb9dc20d627c256a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Envía la cadena de mensaje especificado a la ventana de salida del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szMessage`  
 [in] Cadena de mensaje que se muestra en la ventana de salida del depurador.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)