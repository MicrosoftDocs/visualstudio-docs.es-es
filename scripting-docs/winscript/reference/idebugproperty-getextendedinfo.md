---
title: 'Idebugproperty (:: GetExtendedInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130d11c8ed6bb21210d129bb9aace779db3bd54b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562393"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Obtiene información extendida para la propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cInfos`  
 de Recuento de objetos de información ampliada.  
  
 `rgguidExtendedInfo`  
 de Se pasa una matriz de `GUID`s para que se puedan recuperar al mismo tiempo varios elementos de información ampliada.  
  
 `pExtendedInfo`  
 enuncia Devuelve una matriz de `VARIANT`s que se puede utilizar para recuperar la información de la propiedad extendida.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un `HRESULT` válido, normalmente `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz obtiene información extendida para este objeto. La API solo existe con el fin de recuperar información que no se presta por el uso de `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty (Interfaz)](../../winscript/reference/idebugproperty-interface.md)