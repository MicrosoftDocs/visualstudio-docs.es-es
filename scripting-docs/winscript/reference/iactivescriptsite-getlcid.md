---
title: IActiveScriptSite::GetLCID | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6e128f5ac5de11b45af59c83750411c35e6efa7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Recupera el identificador de configuración regional asociado con la interfaz de usuario del host. El motor de scripting, utiliza el identificador para asegurarse de que las cadenas de error y otros elementos de interfaz de usuario generados por el motor aparecen en el idioma adecuado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `plcid`  
 [out] Dirección de una variable que recibe el identificador de configuración regional para los elementos de interfaz de usuario mostrado por el motor de scripting.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_NOTIMPL`|Este método no se implementa. Usar la configuración regional definida por el sistema.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
  
## <a name="remarks"></a>Comentarios  
 Si este método devuelve `E_NOTIMPL`, se debe utilizar el identificador de configuración regional definido por el sistema.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)