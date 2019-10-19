---
title: 'Iactivescriptsiteinterruptpoll (:: QueryContinue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572239"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Permite a un host especificar que un script debe finalizar.  
  
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
|`S_OK`|La llamada se realizó correctamente y el host permite que el script siga ejecutándose.|  
|`S_FALSE`|La llamada se realizó correctamente y el host solicita que finalice el script.|  
  
## <a name="remarks"></a>Comentarios  
 El script hospedado debe finalizar a menos que el valor devuelto del método `QueryContinue` sea `S_OK`. Un valor devuelto de `S_FALSE` indica que el host solicita explícitamente que finalice el script.  
  
 Un host multiproceso puede utilizar el método `IActiveScript::InterruptScriptThread` para finalizar un script.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iactivescriptsiteinterruptpoll (](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)  
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)