---
title: 'IActiveScriptSite:: GetLCID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570742"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Recupera el identificador de configuración regional asociado a la interfaz de usuario del host. El motor de scripting utiliza el identificador para asegurarse de que las cadenas de error y otros elementos de la interfaz de usuario generados por el motor aparecen en el idioma adecuado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `plcid`  
 enuncia Dirección de una variable que recibe el identificador de configuración regional para los elementos de la interfaz de usuario mostrados por el motor de scripting.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_NOTIMPL`|Este método no se implementa. Utilice la configuración regional definida por el sistema.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
  
## <a name="remarks"></a>Comentarios  
 Si este método devuelve `E_NOTIMPL`, se debe usar el identificador de configuración regional definido por el sistema.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)