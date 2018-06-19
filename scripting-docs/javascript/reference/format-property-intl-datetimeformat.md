---
title: Format (propiedad) (Intl.DateTimeFormat) | Documentos de Microsoft
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636595"
---
# <a name="format-property-intldatetimeformat"></a>format (Propiedad, Intl.DateTimeFormat)
Devuelve una función que da formato a una fecha específica de la configuración regional mediante la configuración de formateador de fecha u hora especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dateTimeFormatObj`  
 Obligatorio. El nombre de la `DateTimeFormat` objeto y emplearlo como un formateador.  
  
## <a name="remarks"></a>Comentarios  
 La función devuelta por la `format` propiedad toma un solo argumento, `date`y devuelve una cadena que representa la fecha localizada mediante el uso de las opciones especificadas en el `DateTimeFormat` objeto. El `date` parámetro de la función devuelta debe ser un número, cadena de fecha, o un `Date` objeto. Si `date` es no siempre, la función utiliza [Date.now](../../javascript/reference/date-now-function-javascript.md) como el valor de entrada predeterminado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa un `DateTimeFormat` objeto localizar la fecha "1 de diciembre de 2007" en alemán y formatearlo.  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Intl.DateTimeFormat (Objeto)](../../javascript/reference/intl-datetimeformat-object-javascript.md)