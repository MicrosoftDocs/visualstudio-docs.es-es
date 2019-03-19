---
title: JsDebugPropertyInfo (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8aeb2dcfc116c8c735cda95fc9d7ab9da97cab3b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154574"
---
# <a name="jsdebugpropertyinfo-structure"></a>Estructura JsDebugPropertyInfo
Indica información sobre una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef struct tagJsDebugPropertyInfo{   BSTR name;   BSTR type;   BSTR value;   BSTR fullName;   JS_PROPERTY_ATTRIBUTES attr;} JsDebugPropertyInfo;  
```  
  
## <a name="members"></a>Miembros  
 `name`  
 Nombre de la propiedad.  
  
 `type`  
 Tipo de la propiedad.  
  
 `value`  
 Valor de la propiedad.  
  
 `fullName`  
 Nombre completo de la propiedad.  
  
 `attr`  
 Enumeración que representa los atributos de la propiedad.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)