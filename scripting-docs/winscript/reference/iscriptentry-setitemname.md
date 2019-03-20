---
title: IScriptEntry::SetItemName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d25ac4977f1fca44d63767c372db169f8cb61ea6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160555"
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