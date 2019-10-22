---
title: 'IObjectIdentity (:: IsEqualObject | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571461"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Determina si un objeto es igual que el objeto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `punk`  
 de Dirección del objeto que se va a comparar con el objeto actual.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|Los objetos son iguales.|  
|`S_FALSE`|Los objetos no son iguales.|  
  
## <a name="remarks"></a>Comentarios  
 Una implementación del método `IsEqualObject` solo debe devolver `S_OK` si los objetos son idénticos.  
  
## <a name="see-also"></a>Vea también  
 [IObjectIdentity (Interfaz)](../../winscript/reference/iobjectidentity-interface.md)