---
title: Constantes de SCRIPTTHREADID | Microsoft Docs
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
ms.openlocfilehash: bf1b23b191bda29b00bf29f482332301897f9f37
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575664"
---
# <a name="scriptthreadid-constants"></a>Constantes SCRIPTTHREADID
Se utiliza para especificar el tipo de subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef DWORD SCRIPTTHREADID;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTTHREADID_CURRENT|0xFFFFFFFD|Subproceso que se está ejecutando actualmente.|  
|SCRIPTTHREADID_BASE|0xFFFFFFFE|Subproceso base; es decir, el subproceso en el que se creó la instancia del motor de scripting.|  
|SCRIPTTHREADID_ALL|0xFFFFFFFF|Todos los subprocesos.|  
  
## <a name="remarks"></a>Comentarios  
 `IActiveScript::GetCurrentScriptThreadID`, `IActiveScript::GetScriptThreadID`, `IActiveScript::GetScriptThreadState`y `IActiveScript::InterruptScriptThread`utilizan el tipo de `SCRIPTTHREADID`, pero las constantes solo las pueden usar `IActiveScript::GetScriptThreadState` y `IActiveScript::InterruptScriptThread`.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)   
 [IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)   
 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)