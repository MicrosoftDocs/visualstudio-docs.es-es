---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b450af1437f9522509913d34976e648da31b91fb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843345"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
No se pudo intenta determinar por qué un auto-attach.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszUrl`  
 [in] No se están utilizando; siempre debe establecerse en un valor null.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Estos son otros códigos de retorno típicos:  
  
|Código|Descripción|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|No se puede determinar por qué el servidor remoto no se pudo iniciar la depuración.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|No se pueden depurar en un servidor remoto, posiblemente debido a permisos insuficientes o porque no está habilitado el verbo DEBUG.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|El servidor web se ha bloqueado y está bloqueando el verbo DEBUG, que es necesario para habilitar la depuración.|  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)