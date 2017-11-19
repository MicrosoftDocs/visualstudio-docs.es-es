---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informa al host un error de tiempo de ejecución de secuencia de comandos cuando el proceso de depurar Manager no encuentra a un depurador de script solo en tiempo.  
  
 Para implementar un depurador en el host, debe controlar [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). En función de una acción del usuario, el host puede asociar el depurador y devolver, o devolver el inicio del depurador en el OnScriptErrorDebug `pfEnterDebugger` parámetro. También debe implementar esta interfaz para recibir la notificación sobre el error de tiempo de ejecución, incluso si no hay ningún depuradores externos que se pueden interpretar por el Administrador de procesos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pErrorDebug`  
 [in] El error de tiempo de ejecución que se ha producido.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Si se debe llamar a [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) si el usuario decide continuar sin depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 También debe implementar esta interfaz para obtener una notificación.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebugEx (Interfaz)](../../winscript/reference/iactivescriptsitedebugex-interface.md)