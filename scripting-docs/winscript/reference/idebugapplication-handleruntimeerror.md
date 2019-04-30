---
title: IDebugApplication::HandleRuntimeError | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2c9a8b15b5095ac346ba047d6668aada7647a31
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412435"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Hace que el subproceso actual se bloquea y envía una notificación del error para el IDE del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 [in] Se produjo el error.  
  
 `pScriptSite`  
 [in] El sitio de la secuencia de comandos del subproceso.  
  
 `pbra`  
 [out] Acción necesaria cuando el depurador reanuda la aplicación.  
  
 `perra`  
 [out] Acción necesaria cuando el depurador reanuda la aplicación si se produce un error.  
  
 `pfCallOnScriptError`  
 [out] Marca que es `TRUE` si el motor debe llamar a la `IActiveScriptSite::OnScriptError` método.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un motor de lenguaje llama a este método en el contexto de un subproceso que produce un error de tiempo de ejecución. Este método hace que el subproceso actual se bloquea y envía una notificación de error para enviarse a la IDE del depurador. Cuando reanuda la aplicación en el IDE del depurador, este método devuelve con la acción que se realizará.  
  
> [!NOTE]
> Mientras se encuentra en el error de tiempo de ejecución, el motor de lenguaje puede llamarse mediante el subproceso para realizar tareas tales como enumerar los marcos de pila o evaluar expresiones.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug (interfaz)](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION (enumeración)](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION (Enumeración)](../../winscript/reference/errorresumeaction-enumeration.md)