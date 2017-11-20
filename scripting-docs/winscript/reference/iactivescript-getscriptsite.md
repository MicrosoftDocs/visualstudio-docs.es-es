---
title: IActiveScript::GetScriptSite | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 961483d45c72018bc216306d6c1aba0400a367ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Recupera el objeto de sitio asociado con el motor de scripts de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] Identificador de la interfaz solicitada.  
  
 `ppvSiteObject`  
 [out] Dirección de la ubicación que recibe el puntero de interfaz al objeto de sitio del host.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_NOINTERFACE`|No se admite la interfaz especificada.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`S_FALSE`|No se ha establecido ningún sitio; el `ppvSiteObject` parámetro está establecido en `NULL`.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)