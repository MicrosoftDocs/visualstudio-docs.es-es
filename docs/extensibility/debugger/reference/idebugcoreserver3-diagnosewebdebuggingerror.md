---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Documentos de Microsoft
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
ms.openlocfilehash: d0facdbd5da7d17061039e0a9e7faed2be3bbe4b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Errores en los intentos para determinar por qué un auto-attach.  
  
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. Los siguientes son otros códigos de retorno típicos:  
  
|Código|Descripción|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|No se puede determinar por qué el servidor remoto no se pudo iniciar la depuración.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|No se pueden depurar en un servidor remoto, posiblemente debido a permisos insuficientes o porque no está habilitado el verbo DEBUG.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|El servidor web se ha bloqueado y está bloqueando el verbo DEBUG, que es necesario para habilitar la depuración.|  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)