---
title: "getTime (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="gettime-method-date-javascript"></a>getTime (Método, Date de JavaScript)
Obtiene el valor de tiempo en milisegundos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el número de milisegundos entre la medianoche del 1 de enero de 1970 y el valor de tiempo en el `Date` objeto. El intervalo de fechas es aproximadamente, 285.616 años de cada lado de la medianoche del 1 de enero de 1970. Los números negativos indican fechas anteriores a 1970.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se realiza varios cálculos de fecha y hora, puede definir variables iguales al número de milisegundos de un día, hora o minuto. Por ejemplo:  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Vea [calcular fechas y horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) para obtener más información sobre cómo usar el `getTime` método.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `getTime`.  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [setTime (Método, Date)](../../javascript/reference/settime-method-date-javascript.md)