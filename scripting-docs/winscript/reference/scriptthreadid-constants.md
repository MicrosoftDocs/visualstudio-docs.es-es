---
title: SCRIPTTHREADID (constantes) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADID
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADID
ms.assetid: 1df9940c-ad0c-42d8-96b9-6a6abe2382e6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfbb39d10d552141a68d40a7be3f1715a80f8f57
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158057"
---
# <a name="scriptthreadid-constants"></a>Constantes SCRIPTTHREADID
Se usa para especificar el tipo de subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|El subproceso actualmente en ejecución.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|El subproceso base; es decir, se crea una instancia en el subproceso en el que el scripting del motor.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Todos los subprocesos.|  
  
## <a name="remarks"></a>Comentarios  
 El `SCRIPTTHREADID` tipo lo utilizan los `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`, y `IActiveScript::InterruptScriptThread`, pero solo se pueden usar las constantes por `IActiveScript::GetScriptThreadState` y `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)