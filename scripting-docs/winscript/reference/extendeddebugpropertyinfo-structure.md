---
title: ExtendedDebugPropertyInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee06b0ace93f068e0530a3aa62b8c28d11069f44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641335"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo (Estructura)
Extiende el `DebugPropertyInfo` estructura con miembros adicionales para caracterizar la propiedad extendida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Miembros  
 `dwValidFields`  
 Un tipo de datos enumerados que se usa para especificar qué campos se inicializan.  
  
 `bstrName`  
 El nombre de propiedad dentro de un contexto.  
  
 `bstrType`  
 El tipo de propiedad como cadena con formato.  
  
 `bstrValue`  
 El valor de propiedad como una cadena con formato.  
  
 `bstrFullName`  
 Nombre completo de la propiedad.  
  
 `dwAttrib`  
 Una enumeración que especifica las marcas para los atributos de propiedad de depuración.  
  
 `pDebugProp`  
 `IDebugProperty`objeto que corresponde a este `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 El identificador de envío.  
  
 `nType`  
 El tipo de propiedad extendida.  
  
 `varValue`  
 El valor de propiedad extendida si pueden caber en la variante.  
  
 `plbValue`  
 Los bytes de datos reales del valor de propiedad.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty`objeto que corresponde a este `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Vea también  
 [DebugPropertyInfo (estructura)](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty (interfaz)](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty (interfaz)](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)