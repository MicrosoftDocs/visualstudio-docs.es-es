---
title: IActiveScript::GetScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 85b7d94ccb9e2589b10bf705721fc289df9638a9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094164"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Recupera el objeto de sitio asociado con el motor de scripts de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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