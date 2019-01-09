---
title: IActiveScript::GetScriptState | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a64067679e1c56831002494c579ffdeba84a1abe
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096582"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Recupera el estado actual del motor de scripting. Este método se pueda llamar desde subprocesos no son de base sin resultante en una llamada que no sea de base a los objetos de host o a la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pss`  
 [out] Dirección de una variable que recibe un valor definido en el [SCRIPTSTATE (enumeración)](../../winscript/reference/scriptstate-enumeration.md) enumeración. El valor indica el estado actual del motor de scripting asociado al subproceso que realiza la llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_POINTER` si se ha especificado un puntero no válido.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)