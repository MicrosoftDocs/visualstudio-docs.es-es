---
title: IDebugProperty::EnumMembers | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 527bf9d3c51dad8ffe1645dc42081dc54189ad7b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979167"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Enumera a los miembros de una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFieldSpec`  
 [in] Especifica el `DBGPROP_INFO_FLAGS` constantes que determinan cuáles son los campos en las estructuras de propiedad enumerada de depuración que deben rellenarse.  
  
 `nRadix`  
 [in] Base para su uso en la interpretación de toda la información numérica.  
  
 `refiid`  
 [in] Se pasa este IID para filtrar el enumerador. El IID es uno de los `IDebugPropertyEnumType` interfaces que heredan de `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Devuelve el `IEnumDebugPropertyInfo` interfaz que enumera las propiedades de miembro.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty (interfaz)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType_All (interfaz)](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo (Interfaz)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)