---
title: IActiveScript::Close | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Close
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Close
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c90b5d089ea6665060944e0a6f720a43aa1295a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640975"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Hace que el motor de scripting abandonar cualquier secuencia de comandos cargado actualmente, perder su estado y la versión de los punteros de interfaz que tiene a otros objetos, y, por tanto, entra en un estado cerrado. Receptores de eventos, el texto de la secuencia de comandos ejecutada inmediatamente y llamadas de macro que ya están en curso se completan antes de los cambios de estado (usar [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) para cancelar un subproceso en ejecución de secuencia de comandos). El host de creación debe llamar a este método antes del lanzamiento de la interfaz para evitar problemas de referencia circular.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|`S_OK`|Correcto.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting ya estaba en estado cerrado).|  
|`OLESCRIPT_S_PENDING`|El método se puso en cola correctamente, pero todavía no ha cambiado el estado. Cuando los cambios de estado, el sitio es vuelva a llamar en el [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) método.|  
|`S_FALSE`|El método se realizó correctamente, pero ya se ha cerrado la secuencia de comandos.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)