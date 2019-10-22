---
title: 'Idebugapplication (:: HandleRuntimeError | Microsoft Docs'
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
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574333"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Hace que el subproceso actual se bloquee y envíe una notificación del error al IDE del depurador.  
  
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
 de Error que se ha producido.  
  
 `pScriptSite`  
 de El sitio de script del subproceso.  
  
 `pbra`  
 enuncia Acción que se realizará cuando el depurador reanude la aplicación.  
  
 `perra`  
 enuncia Acción que se realizará cuando el depurador reanude la aplicación si se produce un error.  
  
 `pfCallOnScriptError`  
 enuncia Marca que es `TRUE` si el motor debe llamar al método `IActiveScriptSite::OnScriptError`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un motor de lenguaje llama a este método en el contexto de un subproceso que produce un error en tiempo de ejecución. Este método hace que el subproceso actual se bloquee y envíe una notificación de error que se enviará al IDE del depurador. Cuando el IDE del depurador reanuda la aplicación, este método devuelve con la acción que se va a realizar.  
  
> [!NOTE]
> En el error en tiempo de ejecución, el subproceso puede llamar al motor de lenguaje para realizar tareas como enumerar marcos de pila o evaluar expresiones.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugapplication (](../../winscript/reference/idebugapplication-interface.md)  
 @No__t_1 de la [interfaz iactivescripterrordebug (](../../winscript/reference/iactivescripterrordebug-interface.md)  
 @No__t_1 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)  
 @No__t_1 [enumeración breakresumeaction (](../../winscript/reference/breakresumeaction-enumeration.md)  
 [ERRORRESUMEACTION (Enumeración)](../../winscript/reference/errorresumeaction-enumeration.md)