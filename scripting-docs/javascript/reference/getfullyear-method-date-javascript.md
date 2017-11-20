---
title: "getFullYear (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- Date object
- getFullYear method
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 211d6c86435e39eb75b9b1ce3415738541ca07db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="getfullyear-method-date-javascript"></a>getFullYear (Método, Date de JavaScript)
Obtiene el año, utilizando la hora local.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getFullYear()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 El año como un número de cuatro dígitos. Por ejemplo, el año 1976 se devuelve como 1976. Años especificados con dos dígitos en el `Date` constructor o en `setFullYear` se consideran del siglo XX, por lo que tiene "5/14/12", `getFullYear` devuelve "1912".  
  
## <a name="remarks"></a>Comentarios  
 Para obtener el año mediante la hora Universal coordinada (UTC), use el `getUTCFullYear` método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **getFullYear** método.  
  
```JavaScript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getUTCFullYear (método, Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear (método, Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear (Método, Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)