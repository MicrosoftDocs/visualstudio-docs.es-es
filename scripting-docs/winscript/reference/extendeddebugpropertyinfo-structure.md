---
title: Estructura Extendeddebugpropertyinfo (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575835"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo (Estructura)
Extiende la estructura de `DebugPropertyInfo` con miembros adicionales para caracterizar la propiedad extendida.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 Un tipo de datos enumerado que se usa para especificar los campos que se van a inicializar.  
  
 `bstrName`  
 Nombre de la propiedad dentro de un contexto.  
  
 `bstrType`  
 El tipo de propiedad como cadena con formato.  
  
 `bstrValue`  
 Valor de la propiedad como una cadena con formato.  
  
 `bstrFullName`  
 Nombre completo de la propiedad.  
  
 `dwAttrib`  
 Una enumeración que especifica las marcas de los atributos de la propiedad de depuración.  
  
 `pDebugProp`  
 `IDebugProperty` objeto que corresponde a este `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 Identificador de envío.  
  
 `nType`  
 Tipo de propiedad extendida.  
  
 `varValue`  
 Valor de la propiedad extendida si puede caber en VARIANT.  
  
 `plbValue`  
 Bytes de datos reales del valor de propiedad.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` objeto que corresponde a este `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [estructura debugpropertyinfo (](../../winscript/reference/debugpropertyinfo-structure.md)  
 @No__t_1 de la [interfaz idebugproperty (](../../winscript/reference/idebugproperty-interface.md)  
 @No__t_1 de la [interfaz idebugextendedproperty (](../../winscript/reference/idebugextendedproperty-interface.md)  
 @No__t_1 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)