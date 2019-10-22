---
title: 'IActiveScript:: SetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575329"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informa al motor de scripting del sitio de la interfaz [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) proporcionado por el host. Llame a este método antes de que se use cualquier otro método de la interfaz [IActiveScript](../../winscript/reference/iactivescript.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pScriptSite`  
 de Dirección del sitio de script proporcionado por el host que se va a asociar a esta instancia del motor de scripting. El sitio debe asignarse de forma única a esta instancia del motor de scripting; no se puede compartir con otros motores de scripting.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_FAIL`|Se produjo un error no especificado. el motor de scripting no pudo finalizar la inicialización del sitio.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, ya se ha establecido un sitio).|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)