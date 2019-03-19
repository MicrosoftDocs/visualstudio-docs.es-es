---
title: Enumeración JS_PROPERTY_ATTRIBUTES | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27aaadfd1d3ff38e9a0382ff1863b73d2bccc325
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153492"
---
# <a name="jspropertyattributes-enumeration"></a>Enumeración JS_PROPERTY_ATTRIBUTES
Indica los atributos de una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Miembros  
  
|Name|Descripción|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|La propiedad no tiene atributos.|  
|`JS_PROPERTY_HAS_CHILDREN`|La propiedad tiene elementos secundarios.|  
|`JS_PROPERTY_FAKE`|La propiedad representa un nodo ficticio, como "[métodos]".|  
|`JS_PROPERTY_METHOD`|La propiedad es un método.|  
|`JS_PROPERTY_READONLY`|La propiedad es de solo lectura.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|La propiedad es un puntero a un objeto nativo de WinRT.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)