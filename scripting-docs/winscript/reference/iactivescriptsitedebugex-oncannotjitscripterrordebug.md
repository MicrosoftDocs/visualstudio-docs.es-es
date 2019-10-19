---
title: 'Iactivescriptsitedebugex (:: OnCanNotJITScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572184"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informa al host sobre un error de script en tiempo de ejecución cuando el administrador de depuración de procesos no encuentra un depurador de script Just-in-Time.  
  
 Para implementar un depurador en el host, debe controlar [iactivescriptsitedebug (:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). En función de una acción del usuario, el host puede adjuntar el depurador y devolver, o bien devolver el inicio del depurador en el parámetro OnScriptErrorDebug `pfEnterDebugger`. También debe implementar esta interfaz para obtener la notificación sobre el error en tiempo de ejecución, aunque no haya ningún depurador externo que el administrador de depuración de procesos pueda interpretar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pErrorDebug`  
 de Error en tiempo de ejecución que se ha producido.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 enuncia Indica si se debe llamar a [iactivescriptsitedebug (:: OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) si el usuario decide continuar sin depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 También debe implementar esta interfaz para obtener una notificación.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebugEx (Interfaz)](../../winscript/reference/iactivescriptsitedebugex-interface.md)