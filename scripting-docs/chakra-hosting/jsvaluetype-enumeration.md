---
title: Enumeración JsValueType | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsValueType
helpviewer_keywords:
- JsValueType enumeration
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4f61cf9118c19a0fc35e7505af422b812d0b43
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569055"
---
# <a name="jsvaluetype-enumeration"></a>JsValueType (Enumeración)
El tipo JavaScript de un JsValueRef.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum JsValueType {  
    JsUndefined      = 0,  
    JsNull           = 1,  
    JsNumber         = 2,  
    JsString         = 3,  
    JsBoolean        = 4,  
    JsObject         = 5,  
    JsFunction       = 6,  
    JsError          = 7,  
    JsArray          = 8,  
    JsSymbol         = 9,  
    JsArrayBuffer    = 10,  
    JsTypedArray     = 11,  
    JsDataView       = 12,  
};  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`JsUndefined`|El valor es el valor `undefined`.|  
|`JsNull`|El valor es el valor `null`.|  
|`JsNumber`|El valor es un valor numérico de JavaScript.|  
|`JsString`|El valor es un valor de cadena de JavaScript.|  
|`JsBoolean`|El valor es un valor booleano de JavaScript.|  
|`JsObject`|El valor es un valor de objeto de JavaScript.|  
|`JsFunction`|El valor es un valor de objeto de función de JavaScript.|  
|`JsError`|El valor es un valor de objeto de error de JavaScript.|  
|`JsArray`|El valor es un valor de objeto de matriz de JavaScript.|  
|`JsSymbol`|El valor es un valor de símbolo de JavaScript.<br /><br /> Este valor de enumeración solo se admite en modo de borde.|  
|`JsArrayBuffer`|El valor es un valor de objeto `ArrayBuffer` de JavaScript.<br /><br /> Este valor de enumeración solo se admite en modo de borde.|  
|`JsTypedArray`|El valor es un valor de objeto de matriz con tipo de JavaScript.<br /><br /> Este valor de enumeración solo se admite en modo de borde.|  
|`JsDataView`|El valor es un valor de objeto `DataView` de JavaScript.<br /><br /> Este valor de enumeración solo se admite en modo de borde.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)