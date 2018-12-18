---
title: IScriptEntry::SetItemName | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 483d3cdc1c8b8de9342003a99427fc2c727ad67f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729305"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Establece el nombre del elemento que identifica un `IScriptEntry` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `psz`  
 [in] La dirección de un búfer que contiene el nombre del elemento. El nombre del elemento se usa el host para identificar la entrada.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|El método no se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Para `IScriptEntry` objetos, este método devuelve `S_OK`.  
  
 Para `IScriptScriptlet` objetos (que derivan de `IScriptEntry`), este método devuelve `E_FAIL`. Para `IScriptScriptlet` objetos, Establece el nombre del elemento [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) y no se puede cambiar.  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (interfaz)](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)