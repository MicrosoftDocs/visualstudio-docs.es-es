---
title: "toLocaleString (método) (objeto) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-method-object-javascript"></a>toLocaleString (Método, Object de JavaScript)
Devuelve una fecha convertida en una cadena con la configuración regional actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido `dateObj` es cualquier `Date` objeto.  
  
 El `toLocaleString` método devuelve un `String` objeto que contiene la fecha escrita en formato largo predeterminado de la configuración regional actual.  
  
-   Para las fechas entre 1601 y 1999 D.C., la fecha tiene el formato según la configuración Regional del Panel de Control del usuario.  
  
-   Para las fechas fuera de este intervalo, el formato predeterminado de la **toString** se utiliza el método.  
  
 Por ejemplo, en los Estados Unidos, `toLocaleString` devuelve "/ 01/05/96 00:00:00" para el 5 de enero. En Europa, devuelve "/ 05/01/96 00:00:00" para la misma fecha, como convención Europea coloca el día anterior al mes.  
  
> [!NOTE]
>  `toLocaleString`solo debe usarse para mostrar los resultados a un usuario; lo nunca debe utilizarse como base para el cálculo en un script como el resultado devuelto es específico del equipo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `toLocaleString`.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [objeto Array](../../javascript/reference/array-object-javascript.md)&#124; [Fecha objeto](../../javascript/reference/date-object-javascript.md)&#124; [Número objeto](../../javascript/reference/number-object-javascript.md)&#124; [Objeto Object](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [toLocaleDateString (Método, Date)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)