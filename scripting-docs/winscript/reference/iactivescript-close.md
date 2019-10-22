---
title: 'IActiveScript:: Close | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f858de42ef2948d218aac6c3194cc6af544da5e9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575780"
---
# <a name="iactivescriptclose"></a>IActiveScript::Close
Hace que el motor de scripting abandone cualquier script cargado actualmente, pierda su estado y libere los punteros de interfaz que tenga en otros objetos, con lo que se especifica un estado cerrado. Los receptores de eventos, el texto de script ejecutado inmediatamente y las invocaciones de macro que ya están en curso se completan antes de que cambie el estado (use [IActiveScript:: InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) para cancelar un subproceso de script en ejecución). El host de creación debe llamar a este método antes de que se libere la interfaz para evitar problemas de referencia circulares.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Close(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor|Significado|  
|-----------|-------------|  
|`S_OK`|Correcto.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting ya estaba en estado cerrado).|  
|`OLESCRIPT_S_PENDING`|El método se puso en cola correctamente, pero el estado todavía no ha cambiado. Cuando el estado cambia, el sitio se debe volver a llamar en el método [IActiveScriptSite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) .|  
|`S_FALSE`|El método se realizó correctamente, pero el script ya se ha cerrado.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)