---
title: 'IActiveScript:: Setscriptsite | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b2a96732e904c7249dc5228ef414c3315012ec56
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097440"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Notifica al motor de scripting de la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) sitio de interfaz proporcionado por el host. Llame a este método antes que cualquier otro [IActiveScript](../../winscript/reference/iactivescript.md) se usa los métodos de interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pScriptSite`  
 [in] Dirección del sitio proporcionada por el host de script que se asociará con esta instancia del motor de scripting. El sitio debe asignarse de forma exclusiva a esta instancia del motor de scripting; no se puede compartir con otros motores de scripting.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_FAIL`|Se produjo un error no especificado; el motor de scripting no pudo finalizar la inicialización del sitio.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, ya se ha establecido un sitio).|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)