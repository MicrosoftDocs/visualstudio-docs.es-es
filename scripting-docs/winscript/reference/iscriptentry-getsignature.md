---
title: 'Iscriptentry (:: Getsignature (| Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575418"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Devuelve información de tipo para un objeto de función de `IScriptEntry`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppti`  
 enuncia Información de tipo asociada a este objeto de función de `IScriptEntry`.  
  
 `piMethod`  
 enuncia Índice del método en el objeto `ITypeInfo`.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 La información de tipo se establece mediante [iscriptentry (:: SetSignature](../../winscript/reference/iscriptentry-setsignature.md) o [Iscriptnode (:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). La entrada también puede generar la información de tipo basándose en la representación interna de la función.  
  
## <a name="see-also"></a>Vea también  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)