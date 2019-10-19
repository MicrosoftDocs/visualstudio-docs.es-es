---
title: 'Iscriptentry (:: SetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetName
ms.assetid: dfa33450-87d7-4c8e-bfd8-0cc2d6542a0e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9dfa27c6c8c58c0ee1599e17e1da5b5f424e416
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575353"
---
# <a name="iscriptentrysetname"></a>IScriptEntry::SetName
En el caso de las entradas que representan un solo objeto (como una función), establece el nombre del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `psz`  
 de Nuevo nombre del objeto `IScriptEntry`.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iscriptentry (](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)