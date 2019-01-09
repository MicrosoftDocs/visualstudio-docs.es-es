---
title: IScriptEntry::SetItemName | Microsoft Docs
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
ms.openlocfilehash: 20af0975a4175d10b110ac5e3cef9e0055f4ce1b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097765"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Establece el nombre del elemento que identifica un `IScriptEntry` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `psz`  
 [in] La dirección de un búfer que contiene el nombre del elemento. El nombre del elemento se usa el host para identificar la entrada.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
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