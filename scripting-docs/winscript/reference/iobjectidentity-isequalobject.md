---
title: IObjectIdentity::IsEqualObject | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e386055e458568f8d4076a37489b7b2397f399
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Determina si un objeto es igual al objeto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `punk`  
 [in] Dirección del objeto que se va a comparar con el objeto actual.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|Los objetos son iguales.|  
|`S_FALSE`|Los objetos no son iguales.|  
  
## <a name="remarks"></a>Comentarios  
 Una implementación de la `IsEqualObject` método debe devolver `S_OK` solo si los objetos son idénticos.  
  
## <a name="see-also"></a>Vea también  
 [IObjectIdentity (Interfaz)](../../winscript/reference/iobjectidentity-interface.md)