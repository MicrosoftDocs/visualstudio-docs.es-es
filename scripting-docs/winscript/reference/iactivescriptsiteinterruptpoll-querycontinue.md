---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93323d500ae7e99957c365d60741fa612ba0fc34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Permite a un host especificar que debe finalizar una secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|La llamada se realizó correctamente y el host permite que la secuencia de comandos continuará ejecutándose.|  
|`S_FALSE`|La llamada se realizó correctamente y las solicitudes de host que finalizan la secuencia de comandos.|  
  
## <a name="remarks"></a>Comentarios  
 El script hospedado debe finalizar a menos que el valor devuelto de la `QueryContinue` método es `S_OK`. Un valor devuelto de `S_FALSE` indica que el host solicita explícitamente que finalizar la secuencia de comandos.  
  
 Puede usar un host multiproceso el `IActiveScript::InterruptScriptThread` método para finalizar una secuencia de comandos.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteInterruptPoll (interfaz)](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)