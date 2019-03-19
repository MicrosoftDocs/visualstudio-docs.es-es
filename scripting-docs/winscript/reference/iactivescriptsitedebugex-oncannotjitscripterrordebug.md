---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs
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
ms.openlocfilehash: 4c643478da37b5a66c22b201ef8f8248df02e4ec
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154483"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informa al host un error de tiempo de ejecución de secuencia de comandos cuando el proceso de administrador de depuración no encuentra a un depurador de scripts solo en tiempo.  
  
 Para implementar un depurador en el host, se debe controlar [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). En función de una acción del usuario, el host puede adjuntar el depurador y devolver, o devolver el inicio del depurador en el OnScriptErrorDebug `pfEnterDebugger` parámetro. También se debe implementar esta interfaz para recibir la notificación sobre el error de tiempo de ejecución, incluso si no hay ningún depuradores externos que se pueden interpretar mediante el Administrador de procesos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pErrorDebug`  
 [in] Error de tiempo de ejecución que se ha producido.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Si se debe llamar a [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) si el usuario decide continuar sin depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 También se debe implementar esta interfaz para recibir una notificación.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebugEx (Interfaz)](../../winscript/reference/iactivescriptsitedebugex-interface.md)