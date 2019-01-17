---
title: IActiveScript::Close | Microsoft Docs
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
ms.openlocfilehash: 886ab1c4c39cf7c64571862bfd28f2fbd1062694
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348808"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Hace que el motor de scripting abandonar cualquier script cargado actualmente, pierden su estado y liberar los punteros de interfaz que tiene a otros objetos, escribir, por tanto, un estado cerrado. Receptores de eventos, el texto de secuencia de comandos ejecutada inmediatamente y llamadas de macro que ya están en curso se completan antes de los cambios de estado (use [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) para cancelar un subproceso en ejecución del script). Este método debe llamarse por el host crear antes de que se libere la interfaz para evitar problemas de la referencia circular.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|`S_OK`|Correcto.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting ya estaba en estado cerrado).|  
|`OLESCRIPT_S_PENDING`|El método se puso en cola correctamente, pero aún no ha cambiado el estado. Cuando los cambios de estado, el sitio es volver a llamar en el [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) método.|  
|`S_FALSE`|El método se realizó correctamente, pero ya se ha cerrado la secuencia de comandos.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)