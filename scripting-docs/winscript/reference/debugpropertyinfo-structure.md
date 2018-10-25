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
ms.openlocfilehash: 0dca3dac5c2e55e512bd4f798ca4a9bce82f7e00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49874194"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo (Estructura)
Describe un objeto de una naturaleza jerárquica que tiene el nombre, tipo y valor. Se utiliza para describir las propiedades de depuración de las variables locales, parámetros, las variables de inspección y expresiones y se registra.  
  
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