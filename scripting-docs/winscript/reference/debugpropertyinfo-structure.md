---
title: DebugPropertyInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47c0f6a359341d19b99c1ce8c099ebf1c6d6a1ff
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088990"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo (Estructura)
Describe un objeto de una naturaleza jerárquica que tiene el nombre, tipo y valor. Se utiliza para describir las propiedades de depuración de las variables locales, parámetros, las variables de inspección y expresiones y se registra.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 Un tipo de datos enumerados que se utiliza para especificar qué campos se inicializan.  
  
 bstrName  
 El nombre de propiedad dentro de un contexto.  
  
 bstrType parámetro  
 El tipo de propiedad, como cadena con formato.  
  
 bstrValue parámetro  
 El valor de propiedad, como cadena con formato.  
  
 bstrFullName  
 Nombre completo de la propiedad.  
  
 dwAttrib  
 Una enumeración que especifica las marcas para los atributos de propiedad de depuración.  
  
 pDebugProp  
 El `IDebugProperty` descrito por la información de este `DebugPropertyInfo` estructura.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty (interfaz)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)