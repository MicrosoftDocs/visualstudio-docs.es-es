---
title: "valueOf (método, Date) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87c5e6ea3c3e28d866f7cabf92dc97b81703b5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-date"></a>valueOf (Método, Date)
Devuelve el valor de hora almacenado en milisegundos desde la medianoche del 1 de enero de 1970 UTC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
date.valueOf()  
```  
  
#### <a name="parameters"></a>Parámetros  
 La `date` objeto es cualquier instancia de una fecha.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor de hora almacenado en milisegundos desde la medianoche del 1 de enero de 1970 UTC. Este es el mismo valor que `getTime`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `valueOf` método con una fecha.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]