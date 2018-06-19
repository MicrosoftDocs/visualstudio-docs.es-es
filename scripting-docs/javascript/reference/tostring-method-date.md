---
title: toString (método, Date) | Documentos de Microsoft
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640255"
---
# <a name="tostring-method-date"></a>toString (Método, Date)
Devuelve una representación de cadena de una fecha. El formato de la cadena depende de la configuración regional. De EE. UU. Inglés (en-us), es como sigue:  
  
 *día de la semana* *mes* *día* *hora*: *minuto*:*segundo* *zona horaria* *año*  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>Parámetros  
 `date`  
 Obligatorio. La fecha que se va a representar como una cadena.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve la representación de cadena de la fecha.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `toString` método con una fecha.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]