---
title: IActiveScript::SetScriptSite | Documentos de Microsoft
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
ms.openlocfilehash: 11fa9003abb03c42adcbf3a548bb5b90d763a344
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645575"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Notifica al motor de scripting de la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) sitio de la interfaz proporcionada por el host. Llamar a este método antes que cualquier otro [IActiveScript](../../winscript/reference/iactivescript.md) se utiliza métodos de interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pScriptSite`  
 [in] Dirección del sitio de script proporcionado por el host que desee asociar a esta instancia del motor de scripting. El sitio debe asignarse de forma exclusiva a esta instancia del motor de scripting; estos no se comparten con otros motores de secuencias de comandos.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_FAIL`|Se produjo un error no especificado; el motor de scripting no pudo finalizar la inicialización del sitio.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, ya se estableció un sitio).|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)