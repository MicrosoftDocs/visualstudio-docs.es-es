---
title: "JsValueType (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueType"
helpviewer_keywords: 
  - "JsValueType (enumeración)"
ms.assetid: 6645e723-e554-41fc-b622-ab54ee044b3d
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# JsValueType (Enumeraci&#243;n)
El tipo JavaScript de un JsValueRef.  
  
## Sintaxis  
  
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
  
## Miembros  
  
### Valores  
  
|Nombre|Descripción|  
|------------|-----------------|  
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
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)