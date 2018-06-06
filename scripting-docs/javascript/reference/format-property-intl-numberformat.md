---
title: Format (propiedad) (Intl.NumberFormat) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7528c79852c4836dfd967322b876d738f9781107
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572480"
---
# <a name="format-property-intlnumberformat"></a>format (Propiedad, Intl.NumberFormat)
Devuelve una función que da formato a un número específico de la configuración regional mediante la configuración del formateador de número especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>Parámetros  
 `numberFormatObj`  
 Requerido. El nombre de la `NumberFormat` objeto y emplearlo como un formateador.  
  
## <a name="remarks"></a>Comentarios  
 La función devuelta por la `format` propiedad toma un solo argumento, `value`y devuelve una cadena que representa el número localizado mediante el uso de las opciones especificadas en el `NumberFormat` objeto. Si `value` no se proporciona, la función devuelve `NaN` (no un número).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa un `NumberFormat` objeto que se va a crear un número localizado.  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigits: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Intl.NumberFormat (Objeto)](../../javascript/reference/intl-numberformat-object-javascript.md)