---
title: 'Iscriptentry (:: SetItemName | Microsoft Docs'
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
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575367"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Establece el nombre de elemento que identifica un objeto `IScriptEntry`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `psz`  
 de Dirección de un búfer que contiene el nombre del elemento. El host usa el nombre del elemento para identificar la entrada.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_FAIL`|El método no se ha realizado correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Para los objetos `IScriptEntry`, este método devuelve `S_OK`.  
  
 Para los objetos `IScriptScriptlet` (que se derivan de `IScriptEntry`), este método devuelve `E_FAIL`. Para los objetos `IScriptScriptlet`, el nombre del elemento se establece mediante [iactivescriptauthor (:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) y no se puede cambiar.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iscriptentry (](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)