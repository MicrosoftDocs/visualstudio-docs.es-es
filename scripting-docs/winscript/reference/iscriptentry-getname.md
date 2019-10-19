---
title: 'Iscriptentry (:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c99cda48a20efb41b2535645ccdb50be8bb6d6bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575451"
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
En el caso de las entradas que representan un único objeto (como una función), devuelve el nombre del objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstr`  
 enuncia Nombre del objeto representado por el bloque de script de `IScriptEntry`. Si una entrada no representa un único objeto, se devuelve NULL.  
  
 Las entradas secundarias representan un único objeto de función.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iscriptentry (](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)