---
title: Estructura Debugpropertyinfo (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575069"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo (Estructura)
Describe un objeto de una naturaleza jerárquica que tiene el nombre, el tipo y el valor. Se utiliza para describir las propiedades de depuración de variables locales, parámetros, variables y expresiones de inspección y registros.  
  
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
 Un tipo de datos enumerado que se usa para especificar los campos que se van a inicializar.  
  
 bstrName  
 Nombre de la propiedad dentro de un contexto.  
  
 bstrType  
 El tipo de propiedad, como una cadena con formato.  
  
 bstrValue  
 Valor de la propiedad, como una cadena con formato.  
  
 bstrFullName  
 Nombre completo de la propiedad.  
  
 dwAttrib  
 Una enumeración que especifica las marcas de los atributos de la propiedad de depuración.  
  
 pDebugProp  
 @No__t_0 descrito por la información de esta estructura de `DebugPropertyInfo`.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugproperty (](../../winscript/reference/idebugproperty-interface.md)  
 @No__t_1 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)