---
title: 'Idebugproperty (:: GetPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0698e09cd9643322a237a81d971248577fd97e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562328"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Obtiene el valor de una `IDebugProperty` que describe un método o una propiedad indizada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 de Especifica las constantes de `DBGPROP_INFO_FLAGS` que determinan los campos que se van a rellenar en la estructura de `DebugPropertyInfo`.  
  
 `nRadix`  
 de Base que se va a utilizar para dar formato a cualquier información numérica.  
  
 `pPropertyInfo`  
 enuncia Devuelve el `DebugPropertyInfo` estructura que describe la propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un `HRESULT` válido, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugproperty (](../../winscript/reference/idebugproperty-interface.md)  
 @No__t_1 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)  
 [DebugPropertyInfo (Estructura)](../../winscript/reference/debugpropertyinfo-structure.md)