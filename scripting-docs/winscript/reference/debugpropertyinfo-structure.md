---
title: DebugPropertyInfo (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9baade1a742a06c952906c05c574e752806bc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo (Estructura)
Describe un objeto de una naturaleza jerárquica con nombre, tipo y valor. Se utiliza para describir las propiedades de depuración de las variables locales, parámetros, variables de inspección y expresiones y se registra.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Miembros  
 dwValidFields  
 Un tipo de datos enumerados que se usa para especificar qué campos se inicializan.  
  
 bstrName  
 El nombre de propiedad dentro de un contexto.  
  
 bstrType parámetro  
 El tipo de propiedad, como cadena con formato.  
  
 bstrValue parámetro  
 El valor de propiedad como cadena con formato.  
  
 bstrFullName  
 Nombre completo de la propiedad.  
  
 dwAttrib  
 Una enumeración que especifica las marcas para los atributos de propiedad de depuración.  
  
 pDebugProp  
 El `IDebugProperty` descrita por la información en este `DebugPropertyInfo` estructura.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty (interfaz)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)