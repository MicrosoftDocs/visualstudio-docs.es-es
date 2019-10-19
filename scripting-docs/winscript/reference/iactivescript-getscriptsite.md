---
title: 'IActiveScript:: GetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 567c7b5c1ead5388e6ec9c67d6ab6f9f580adf20
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575746"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Recupera el objeto de sitio asociado al motor de Windows Script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `iid`  
 de Identificador de la interfaz solicitada.  
  
 `ppvSiteObject`  
 enuncia Dirección de la ubicación que recibe el puntero de interfaz al objeto de sitio del host.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_NOINTERFACE`|No se admite la interfaz especificada.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`S_FALSE`|No se ha establecido ningún sitio; el parámetro `ppvSiteObject` se establece en `NULL`.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)