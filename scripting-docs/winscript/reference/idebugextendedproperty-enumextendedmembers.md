---
title: 'Idebugextendedproperty (:: EnumExtendedMembers | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.EnumExtendedMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6fd225be9504254965eab77b912f50fb5c777e3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576388"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
Enumera los miembros de una propiedad extendida.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFieldSpec`  
 de Especifica las constantes EX_DBGPROP_INFO_FLAGS que determinan los campos de las estructuras de propiedades de depuración extendida enumeradas que se van a rellenar.  
  
 `nRadix`  
 de Base que se va a usar para interpretar cualquier información numérica.  
  
 `ppeepi`  
 enuncia Devuelve la interfaz `IEnumDebugExtendedPropertyInfo` que enumera las propiedades de miembro.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un `HRESULT` válido, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugextendedproperty (](../../winscript/reference/idebugextendedproperty-interface.md)  
 @No__t_1 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)  
 [ExtendedDebugPropertyInfo (Estructura)](../../winscript/reference/extendeddebugpropertyinfo-structure.md)