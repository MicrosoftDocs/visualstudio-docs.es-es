---
title: Función Date.Now (JavaScript) | Documentos de Microsoft
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
helpviewer_keywords:
- now method
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41a098c55b8ced3c630d3724615835301b6f00c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636395"
---
# <a name="datenow-function-javascript"></a>Función Date.now (JavaScript)
Obtiene la fecha y hora actuales.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Date.now()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El número de milisegundos entre la medianoche del 1 de enero de 1970 y la fecha y hora actuales.  
  
## <a name="remarks"></a>Comentarios  
 El [getTime (método)](../../javascript/reference/gettime-method-date-javascript.md) devuelve el número de milisegundos entre el 1 de enero de 1970 y una fecha especificada.  
  
 Para obtener información sobre cómo calcular el tiempo transcurrido y comparar las fechas, vea [calcular fechas y horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `now`.  
  
```JavaScript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## <a name="requirements"></a>Requisitos  
 No se admite en instalado versiones anteriores a Internet Explorer 9. No obstante, es compatible en los siguientes modos de documento: interpretación, estándar de estándares de Internet Explorer 6, estándares de Internet Explorer 7, estándar de Internet Explorer 8, Internet Explorer 9, estándar de Internet Explorer 10. También se admiten en [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicaciones.  
  
## <a name="see-also"></a>Vea también  
 [getTime (método, Date)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date (objeto)](../../javascript/reference/date-object-javascript.md)   
 [Calcular fechas y horas (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Métodos de JavaScript](../../javascript/reference/javascript-methods.md)