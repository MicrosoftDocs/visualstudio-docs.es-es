---
title: IDebugMessageEvent2::GetMessage | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2cb6db61048765ec577a0d14ff4079f78e013219
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Obtiene el mensaje que se mostrará.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pMessageType`  
 [out] Devuelve un valor de la [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumeración que describe el tipo del mensaje.  
  
 `pbstrMessage`  
 [out] Devuelve el mensaje.  
  
 `pdwType`  
 [out] Devuelve el tipo del mensaje, usando las convenciones de Win32 `MessageBox` función. Consulte la [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) función para obtener más información.  
  
 `pbstrHelpFileName`  
 [entrada, salida] Devuelve el nombre de archivo de ayuda. Puede ser un null (C++) o un valor vacío (C#) si no hay ningún archivo de ayuda.  
  
 `pdwHelpId`  
 [entrada, salida] Devuelve el identificador de ayuda. Puede ser 0 si no hay ninguna ayuda asociado a este mensaje.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)