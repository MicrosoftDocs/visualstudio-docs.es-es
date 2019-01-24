---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b43211dca57a404d5625cfc2d7ede67a70a0a40
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087989"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Permite a un host especificar que una secuencia de comandos debe finalizar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|La llamada se realizó correctamente y permite que el host de la secuencia de comandos continúe ejecutándose.|  
|`S_FALSE`|La llamada se realizó correctamente y las solicitudes de host que finalizar la secuencia de comandos.|  
  
## <a name="remarks"></a>Comentarios  
 Debe finalizar el script hospedado, a menos que el valor devuelto de la `QueryContinue` método es `S_OK`. Un valor devuelto de `S_FALSE` indica que el host solicita explícitamente que termina la secuencia de comandos.  
  
 Puede usar un host multiproceso el `IActiveScript::InterruptScriptThread` método para finalizar una secuencia de comandos.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteInterruptPoll (interfaz)](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)