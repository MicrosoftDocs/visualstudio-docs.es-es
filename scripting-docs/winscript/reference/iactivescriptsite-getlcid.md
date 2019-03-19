---
title: IActiveScriptSite::GetLCID | Microsoft Docs
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
ms.openlocfilehash: c6ebcfec9764aae98f7d74ac98e0c88ecec7c4da
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155516"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Recupera el identificador de configuración regional asociado con la interfaz de usuario del host. El motor de scripting utiliza el identificador para asegurarse de que las cadenas de error y otros elementos de interfaz de usuario generados por el motor aparecen en el idioma adecuado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `plcid`  
 [out] Dirección de una variable que recibe el identificador de configuración regional para los elementos de interfaz de usuario mostrada por el motor de scripting.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_NOTIMPL`|Este método no se implementa. Use la configuración regional definido por el sistema.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
  
## <a name="remarks"></a>Comentarios  
 Si este método devuelve `E_NOTIMPL`, se debe usar el identificador definido por el sistema local.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)