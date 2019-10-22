---
title: 'Idebugproperty (:: EnumMembers (| Microsoft Docs'
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
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562422"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Enumera los miembros de una propiedad.  
  
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
 de Especifica las constantes `DBGPROP_INFO_FLAGS` que determinan los campos de las estructuras de propiedades de depuración enumeradas que se van a rellenar.  
  
 `nRadix`  
 de Base que se va a usar para interpretar cualquier información numérica.  
  
 `refiid`  
 de Este IID se pasa para filtrar el enumerador. El IID es una de las interfaces `IDebugPropertyEnumType` que heredan de `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 enuncia Devuelve la interfaz `IEnumDebugPropertyInfo` que enumera las propiedades de miembro.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un `HRESULT` válido, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugproperty (](../../winscript/reference/idebugproperty-interface.md)  
 @No__t_1 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)  
 @No__t_1 de la [interfaz IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)  
 [IEnumDebugPropertyInfo (Interfaz)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)