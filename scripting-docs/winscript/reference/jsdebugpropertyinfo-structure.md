---
title: Estructura JsDebugPropertyInfo | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: JsDebugPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9d2ae0d93729d4c333509e0178f4c4829ebf13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsdebugpropertyinfo-structure"></a>Estructura JsDebugPropertyInfo
Indica información sobre una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagJsDebugPropertyInfo{   BSTR name;   BSTR type;   BSTR value;   BSTR fullName;   JS_PROPERTY_ATTRIBUTES attr;} JsDebugPropertyInfo;  
```  
  
## <a name="members"></a>Miembros  
 `name`  
 Nombre de la propiedad.  
  
 `type`  
 Tipo de la propiedad.  
  
 `value`  
 El valor de la propiedad.  
  
 `fullName`  
 Nombre completo de la propiedad.  
  
 `attr`  
 Enumeración que representa los atributos de la propiedad.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)