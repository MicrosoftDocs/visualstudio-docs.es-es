---
title: IDebugApplication::HandleRuntimeError | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Hace que el subproceso actual se bloquee y envía una notificación del error para el IDE del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pErrorDebug`  
 [in] El error que se ha producido.  
  
 `pScriptSite`  
 [in] El sitio de la secuencia de comandos del subproceso.  
  
 `pbra`  
 [out] Acción a realizar cuando el depurador reanuda la aplicación.  
  
 `perra`  
 [out] Acción a realizar cuando el depurador reanuda la aplicación si se produce un error.  
  
 `pfCallOnScriptError`  
 [out] Marca que es `TRUE` si el motor debe llamar a la `IActiveScriptSite::OnScriptError` método.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un motor de lenguaje llama a este método en el contexto de un subproceso que causa un error de tiempo de ejecución. Este método hace que el subproceso actual se bloquee y envía una notificación de error que se envía al depurador IDE. Cuando el depurador IDE reanuda la aplicación, este método devuelve a la acción que se debe realizar.  
  
> [!NOTE]
>  Mientras se encuentra en el error de tiempo de ejecución, el motor del lenguaje puede llamarse mediante el subproceso para realizar tareas tales como enumerar los marcos de pila o se evalúan las expresiones.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug (interfaz)](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Enumeración BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION (Enumeración)](../../winscript/reference/errorresumeaction-enumeration.md)